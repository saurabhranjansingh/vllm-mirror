# vllm-mirror

Mirror the official `vllm` Docker images from Docker Hub to GitHub Container Registry (GHCR) for reliable, rate-limit-free pulls across environments.

## What this repo does

- Uses **GitHub Actions** to copy images from `docker.io/vllm/vllm-openai` to `ghcr.io/<OWNER>/vllm-openai`.
- Supports:
  - multiple tags in one run
  - manual runs and scheduled syncs
  - optional login to Docker Hub if you hit anonymous rate limits

## Quick start

1. **Make GHCR usable**
   - In your GitHub account settings, enable **GitHub Packages** and **GHCR**.
   - In this repository, go to **Settings → Actions → General** and ensure workflows can create packages.
   - (Optional) In **Settings → Packages**, set default package visibility to **public** if you want public pulls.

2. **Create optional secrets**
   - `DOCKERHUB_USERNAME` and `DOCKERHUB_TOKEN` (optional, recommended if you hit rate limits).

3. **Run the workflow**
   - Go to **Actions → Mirror vLLM image → Run workflow**.
   - Provide the version (e.g., `v0.11.0, v0.10.3, latest`).
   - The workflow will push to `ghcr.io/<OWNER>/vllm-openai:<tag>`.

## Examples

- Mirror a single tag:
  - `v0.11.0`

## Pulling the mirrored image

```bash
# GHCR requires owner in the path; replace <OWNER> with your GitHub username/org
docker pull ghcr.io/<OWNER>/vllm-openai:v0.11.0
