# orchestrated-task

一个任务 skill：把复杂软件任务整理成由一个常驻主 agent 编排、子 agent 执行的任务文档。主 agent 负责立项、再设计与派发；工作者按步实现并提交检查点；验收者每圈新起、在干净克隆上独立复验；独立评审每次新起，审设计并做运行期复评。状态写在文件里，由 `assets/cycle.mjs` 记录。

不限定执行环境：凡是能让主 agent 启动隔离上下文的子 agent 并与之对话的 agent 都能执行。用户可以按角色指定模型；未指定时由主 agent 决定。

从 [`cycle-runner`](https://github.com/sskyy/cycle-runner)（`cyclic-task-prompt`）派生，改动与依据见 [`assets/README.md`](assets/README.md)。

## 安装

```bash
git clone git@github.com:sskyy/orchestrated-task.git ~/.agents/skills/orchestrated-task
ln -s ~/.agents/skills/orchestrated-task ~/.claude/skills/orchestrated-task
```

## 内容

- `SKILL.md`：skill 入口，生成流程、执行环境要求与运行要点。
- `assets/task-template.md`：任务文件模板（共享规范、任务、模型放置、各角色段）。
- `assets/cycle.mjs`、`assets/cycle.test.mjs`：状态头与账本的 runner 及其测试（`node --test assets/cycle.test.mjs`）。
- `assets/README.md`：模板来源、与 cyclic-task-prompt 的差异及证据、维护要求。
- `references/project-profile-schema.md`：项目画像的格式。
