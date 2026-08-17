# calendar-mcp

Google Calendar 的 Roxy MCP 插件，提供日历工具和主动提醒事件源。

```text
calendar-mcp
├─ plugin.py
└─ mcp
   ├─ run_mcp.py
   ├─ run_server.py
   └─ src
```

插件代码安装到 `~/.roxy-plugin/cache/<marketplace>/calendar/<version>/`，运行数据保存在 `~/.roxy-plugin/data/calendar-<marketplace>/`：

- `.env`：Google OAuth 客户端配置
- `.gcp-saved-tokens.json`：OAuth Token
- `proactive_alerts.json`：主动提醒配置
- `calendar_alerts.sqlite3`：提醒确认状态
- `calendar_mcp.log`：运行日志

首次加载会从 `$ROXY_WORKSPACE/mcp/calendar-mcp/` 复制旧配置和状态；旧
`AKASHIC_WORKSPACE` 只作为已有安装的兼容回退。刷新 OAuth Token 后会立即写回数据目录，
避免每次主动轮询重复刷新。
