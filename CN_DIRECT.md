# 国内优先直连配置

`lazy_group_cn_direct.conf` 基于上游 `lazy_group.conf`，保留原有策略组和服务分流，仅调整国内与未识别流量的兜底行为。

## 导入地址

```text
https://raw.githubusercontent.com/yokin/Shadowrocket/cn-direct/lazy_group_cn_direct.conf
```

在 Shadowrocket 中通过该 URL 下载配置后，将首页的 **全局路由** 设为 **配置**。

## 与上游版本的差异

- 直连域名使用系统 DNS。
- 直连域名解析失败时不回退代理。
- 局域网和中国域名规则先于通用代理规则匹配。
- 中国大陆 IP 继续直连。
- 未匹配流量默认直连。

因此，冷门且未被规则收录的国外网站可能尝试直连；需要时可为具体域名增加 `PROXY` 规则。

## 上游更新

GitHub fork 不会自动同步。仓库的 `main` 分支保持为上游原版，可在仓库页面使用 **Sync fork** 获取 `LOWERTOP/Shadowrocket` 的更新；定制配置保存在 `cn-direct` 分支，避免阻碍 `main` 同步。

同步 `main` 后不会自动更新 `cn-direct`，也不会自动把新版 `lazy_group.conf` 的内容复制进这个派生配置。上游配置发生实质变化后，仍需把 `main` 的更新合入 `cn-direct`，重新比较并更新 `lazy_group_cn_direct.conf`；其中引用的远程规则集则会由 Shadowrocket 在使用或编译配置时更新。
