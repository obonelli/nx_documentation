This guide explains how to create a scalable monorepo with Nx, React, and shareable libraries.
⚡️ Ideal for teams, scalable architectures, and component reuse.

 1. Initialize the Monorepo

npx create-nx-workspace@latest my-org --preset=react-monorepo
cd my-org

2. Understand the Structure

my-org/
├── apps/
│   └── my-org/           # React app
├── libs/                 # Shared libraries live here
├── nx.json
├── project.json
├── tsconfig.base.json
└── ...

3. Create a New App

npx nx generate @nx/react:application store

#for run the store

npx nx serve store

4. Create a Shared Library

npx nx generate @nx/react:library ui

5. Use the Library in the App

import { Button } from '@my-org/ui';

export function App() {
  return (
    <div>
      <h1>Welcome to Store!</h1>
      <Button>Click me</Button>
    </div>
  );
}

 6. Generate a Component in the UI Library

 npx nx g @nx/react:component Button --project=ui

7. Run Tests

npx nx test store     # Test app
npx nx test ui        # Test library

8. Lint & Format

npx nx lint store
npx nx format:write   # Auto-format code

9. Build the App

npx nx build store

10. Optimize and Analyze

npx nx dep-graph

✅ Quick Useful Commands

| Action           | Command                                            |
| ---------------- | -------------------------------------------------- |
| Crear nueva app  | `nx g @nx/react:application app-name`              |
| Crear nueva lib  | `nx g @nx/react:library lib-name`                  |
| Crear componente | `nx g @nx/react:component Comp --project=lib-name` |
| Levantar app     | `nx serve app-name`                                |
| Test unitario    | `nx test project-name`                             |
| Lint             | `nx lint project-name`                             |
| Build            | `nx build app-name`                                |
| Ver dependencias | `nx dep-graph`                                     |
| Formatear código | `nx format:write`                                  |
