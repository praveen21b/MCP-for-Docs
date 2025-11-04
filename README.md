# MCP-for-Docs
apt install hugo -y
hugo new site docs

podman run --rm -it \
  --name docs-mcp-server \
  -p 127.0.0.1:6280:6280 \
  -v /root/MCP-for-Docs/docs-mcp-server:/app \
  -w /app \
  node:20 \
  sh -c "npm install && npm run build && HOST=0.0.0.0 node --enable-source-maps dist/index.js"
