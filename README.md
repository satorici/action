# What is Satori CI?

Satori allows you to assert if your systems and software behave as expected. With this Github Action you can include your checks as part of the local container that Github creates.

## How to Install and Use the Satori CI Action

### 1. Set the `SATORITOKEN` Secret
1. Go to your repository’s **Settings**.
2. Navigate to **Security** > **Secrets and variables** > **Actions**.
3. Click **New repository secret**.
4. Name the secret `SATORITOKEN` and paste your token value from http://satori.ci/user-settings/.
5. Click **Add secret**.

### 2. Create Your Satori CI Action Workflow File
In your repository, create `.github/workflows/satori-ci.yml`:

```name: Satori CI Test
on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Satori CI - Automated Testing
        uses: satorici/action@v1.0.0
        env:
          SATORITOKEN: ${{ secrets.SATORITOKEN }}
```

### 3. Commit and Push Your Changes
Commit the workflow file and push it to your main branch (or the desired branch). GitHub Actions will detect and run the workflow on the next push event.

### 4. Verify the Workflow Execution
Check the **Actions** tab in your repository to view the logs and ensure the action ran successfully.
