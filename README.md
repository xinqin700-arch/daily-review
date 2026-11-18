# daily-review 📅

一个 WorkBuddy Skill：把你的语音复盘整理成结构化的 Obsidian 日记，自动写入 Daily Notes 目录。

你只需要对着手机/电脑说一段复盘（或粘贴语音转文字），它会：

1. 把口语转成书面语，**保留全部核心信息、不编造、不遗漏**
2. 按固定模板填充（睡眠、感谢、情绪、事项回顾、收获反思……）
3. 语音里没提到的字段**留空**，保持模板完整
4. 自动补全日期、标题、标签（frontmatter + 上次记录时间）
5. 直接写入你的 Obsidian 日记目录，文件名 `DailyYYYY-MM-DD.md`

## 安装

把本仓库的 `SKILL.md` 放入：

- **WorkBuddy（用户级）**：`~/.workbuddy/skills/daily-review/`
- **Claude Code / 其他 Agent**：`~/.claude/skills/daily-review/` 或项目的 `.claude/skills/`

```bash
git clone https://github.com/xinqin700-arch/daily-review.git ~/.workbuddy/skills/daily-review
```

## 首次配置

Skill 不硬编码任何路径。首次运行时按以下顺序解析你的日记目录：

1. 指令中直接给出的目录（如"写入 /path/to/MyVault/Daily"）
2. 环境变量 `DAILY_REVIEW_DIR`
3. 配置文件 `~/.workbuddy/skills/daily-review/config.json`：

```json
{ "daily_dir": "/Users/you/Library/Mobile Documents/iCloud~md~obsidian/Documents/MyVault/Daily" }
```

4. 都没有 → 会询问你一次并记住

## 使用

```
每日复盘，今天睡到10点才起，昨晚刷手机到1点……下午投了20份简历，晚上跑了3公里……
```

生成结果（部分）：

```markdown
---
title: "Daily: 2026-11-01"
date: 2026-11-01 20:00:00
tags: ["daily", "review", "lifeos"]
---
📅 每日复盘：2026-11-01

上次记录：2026-10-31 20:00 | 本次耗时：约 5 分钟

🌙 1. 昨晚睡眠如何？

- 上床时间：2026-10-31 01:00
- 起床时间：2026-11-01 10:00
- 睡眠时长（手表/估算）：约 9 小时
- ...
```

### 日期归属

默认**复盘写入昨天**的日记（适合跨夜复盘的场景）。如果你习惯当天晚上写当天的复盘，把 SKILL.md 中 Step 2 的"目标日期 = 昨天"改为"目标日期 = 今天"即可。

## 模板结构

🌙 睡眠 → 🙏 感谢 → 🧠 情绪 → ✅ 事项回顾（工作/个人成长/健康/家庭）→ 📝 收获与反思

想增删字段直接改 SKILL.md 里的模板段落即可，Agent 会按新模板执行。

## 安全与隐私

- 所有内容只写入你本地的 Obsidian 目录，不经任何第三方
- 若目标日期文件已存在，会先询问再覆盖

## License

MIT
