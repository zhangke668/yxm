# 涌现猫（yxm）

把一句卡住你的困惑丢给喵。喵不急着回答，先把句子里承重的词拆开，看看里面混着几层意思。很多问题拆着拆着就消失了，剩下的会变成一件能查清的事，或者一个今天就能试的小实验。想通之后，喵把这场对话收成一枚有名字的章，存进你的图鉴。

## 安装

把这句话发给你的 agent（Claude Code、Codex、Grok、Trae、豆包等能在电脑上执行命令的都可以）：

```text
帮我安装 https://github.com/zhangke668/yxm
```

装好后新开一个对话，输入 `/yxm`，看到喵的自我介绍就装好了。

## 怎么用

- `/yxm 人生的意义是什么`：拆一句困惑。
- 拆到你觉得对上了，回一句"这下通了"，喵把整场对话复盘一遍；再回"收下"，这枚章就存进图鉴。
- `/yxm 学一个词` 或 `/yxm 学 拖延`：100 个概念词和常见词的三层短课，每层一道判断题。
- 说"我的图鉴"：看收过的章。

图鉴存在你电脑"文档"目录下的 `涌现猫` 文件夹里，没有云端数据库。完整说明见 [skills/yxm/README.md](skills/yxm/README.md)。

## 给 AI agent 的安装说明

用户让你安装这个仓库时，按下面的顺序试，前一步成功就不用做后面的。skill 本体在仓库的 `skills/yxm/` 文件夹里。下文的 `~` 指用户主目录，Windows 上是 `C:\Users\<用户名>`。

### 1. 用 skills 安装器（推荐，需要 Node.js）

```bash
npx -y skills add zhangke668/yxm -g -y
```

它会把 skill 装到 `~/.agents/skills/yxm/`，并自动链接到本机已有的 Claude Code、Grok、Trae 等 agent 目录。输出里如果有 `PromptScript does not support global skill installation`，可以忽略，不影响其他 agent。

### 2. 没有 Node.js，或安装器失败：克隆后复制

把仓库克隆到临时目录，再把里面的 `skills/yxm` 整个文件夹复制到你自己读取 skill 的目录。文件夹名必须是 `yxm`，`SKILL.md` 直接放在里面：

| Agent | 目录 |
|-------|------|
| Claude Code | `~/.claude/skills/yxm/` |
| Grok | `~/.grok/skills/yxm/` |
| Trae / Trae CN | `~/.trae/skills/yxm/` 或 `~/.trae-cn/skills/yxm/` |
| Codex、豆包，以及其他读通用目录的 agent | `~/.agents/skills/yxm/` |

```bash
git clone --depth 1 https://github.com/zhangke668/yxm.git <临时目录>
# 再把 <临时目录>/skills/yxm 复制到上表的目录
```

连不上 GitHub 时，告诉用户网络不通，请用户自己下载 <https://github.com/zhangke668/yxm/archive/refs/heads/main.zip> 发给你，解压后同样只复制 `skills/yxm` 这个文件夹。

### 3. 你不能在电脑上执行命令

比如手机 App 或网页聊天。读取 <https://raw.githubusercontent.com/zhangke668/yxm/main/skills/yxm/SKILL.md>，以及它指向的 `skills/yxm/references/` 里的文件，在当前对话里按它的方法陪用户拆困惑，并告诉用户：这样只在本次对话有效，章存不进图鉴；想长期用，需要装到能执行命令的 agent 里。

### 装完以后

1. 确认 `yxm/SKILL.md` 存在，开头写着 `name: yxm`，同目录下有 `references/` 和 `课程/`。
2. 告诉用户：新开一个对话（或重启 agent）后，输入 `/yxm` 试试。

## 更新和卸载

- 更新：`npx -y skills update yxm -g -y`。手动装的，删掉旧的 `yxm` 文件夹，按上面的步骤重新复制。图鉴在"文档"里，不受影响。
- 卸载：`npx -y skills remove yxm -g -y`；手动装的，直接删掉 `yxm` 文件夹。想连数据一起清掉，再删"文档"里的 `涌现猫` 文件夹。

喵陪你拆困惑，不能代替心理咨询或治疗。如果你正处在危机里，请马上联系身边的人，或拨打心理援助热线 12356。
