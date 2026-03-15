# General Pipelines

Репозиторий с переиспользуемыми GitHub Actions workflows для основных стеков.

## Доступные workflows

### Docker — Build and Push

Сборка и пуш Docker образов в ghcr.io.

**Путь:** `.github/workflows/docker/build-push.yml`

#### Использование

В репозитории с образами создайте `.github/workflows/build.yml`:

```yaml
name: Build and Push

on:
  push:
    tags:
      - 'v*-kotlin'
      - 'v*-react'
      - 'v*-vue'

jobs:
  build:
    uses: poomsae-tech/general-pipelines/.github/workflows/docker/build-push.yml@v1
```

#### Требования

1. **Структура директорий:**
   ```
   kotlin/Dockerfile
   react/Dockerfile
   vue/Dockerfile
   ```

2. **Формат тегов:**
   - `v1.0.0-kotlin` → собирает `./kotlin/Dockerfile`, пушит в `ghcr.io/poomsae-tech/kotlin:v1.0.0`
   - `v1.0.0-react` → собирает `./react/Dockerfile`, пушит в `ghcr.io/poomsae-tech/react:v1.0.0`
   - `v1.0.0-vue` → собирает `./vue/Dockerfile`, пушит в `ghcr.io/poomsae-tech/vue:v1.0.0`

#### Пример запуска

```bash
git tag v1.2.3-kotlin
git push origin v1.2.3-kotlin
```

## Версионирование

Используйте теги (v1, v2) при указании workflow:
- `poomsae-tech/general-pipelines/.github/workflows/docker/build-push.yml@v1`