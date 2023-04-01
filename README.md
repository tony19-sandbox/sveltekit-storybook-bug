# Demo of SvelteKit/Storybook bug

If a story component imports `'$app/navigation'`, SvelteKit emits this error when rendering the story:

```
Cannot read properties of undefined (reading 'disable_scroll_handling')
TypeError: Cannot read properties of undefined (reading 'disable_scroll_handling')
    at http://localhost:6006/node_modules/@sveltejs/kit/src/runtime/app/navigation.js?v=b4aad7c7:14:11
```

## Steps to reproduce

 1. Scaffold new SvelteKit project:

    ```sh
    npm create svelte@latest my-app
    cd my-app
    npm install
    ```

 2. Add Storybook:

    ```sh
    npx storybook@next init
    ```

3. Edit `src/stories/Button.stories.ts` to import `'$app/navigation'`:

    ```html
    <script lang="ts">
      import { goto } from '$app/navigation';
    </script>
    ```

4. Run Storybook:

    ```sh
    npm run storybook
    ```

5. Open the `Button` story in the browser.
