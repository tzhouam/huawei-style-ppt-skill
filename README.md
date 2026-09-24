# 华为风格 PPT Skill

面向中文技术汇报、项目进展、经营分析和方案评审。`ppt-forge` 先核清主张与证据，再根据用户要的交付形态制作：

| 模式 | 交付 | 适用场景 |
|---|---|---|
| 原生可编辑 | PPTX 或 Google Slides | 正式汇报、现有 deck 改稿、需要反复修改文字和流程 |
| 低保真蓝图 | 分页表和 Markdown | 内容规划、尚未确定视觉方向 |
| Raster | 逐页 PNG | 明确要固定画面、视觉概念图或独立图片 |

可编辑演示文稿以原生文本、形状、连线和图表构成；截图与视频可以嵌入，但不会把整页图片称为“可编辑”。现有文件的内容与视觉系统优先，华为式色板作为无参考稿时的默认设计依据。

## 安装

```bash
# Claude Code
cp -r ppt-forge ~/.claude/skills/

# Codex
cp -r ppt-forge ~/.codex/skills/
```

编辑 PPTX 通常需要 Python 与 `python-pptx`，并用 LibreOffice 或同类工具渲染复核。Google Slides 需要宿主提供可用的连接器。Raster 路线需要 imagegen；没有 imagegen 不影响原生 PPTX 路线。

示例：

> 按这份现有 PPTX 的风格，重画可编辑的流程图，插入真实 PR 截图，并检查所有页码和视频。

> 做一套华为式技术汇报，面向部门领导；重点解释问题、方法、实际案例和限制，交付可编辑 PPTX。

## 质量门禁

- 每页有清楚的主张，数据与案例可追溯；团队、产品和执行角色不混用。
- 流程图以真实任务流为准，箭头、共享知识源、人工验收与上线状态均要准确。
- 标题、正文、截图、页码与媒体全稿渲染检查；不靠自动缩字解决信息过载。
- `python ppt-forge/scripts/check_pptx.py deck.pptx` 可以预检明显越界、页码和整页图片；仍须目视检查最终稿。

## 目录

```text
ppt-forge/
├── SKILL.md
├── agents/openai.yaml
├── references/
│   ├── ppt-lofi-authoring.md
│   ├── ppt-style-huawei.md
│   └── native-editable.md
└── scripts/check_pptx.py
```

## 来源与许可

低保真与视觉 preset 源自 [`zts212653/clowder-ai`](https://github.com/zts212653/clowder-ai) 的 PPT Forge（2026-06-17 基线）；本仓库补充了可编辑制作、证据页和交付验收路线。MIT License，见 [LICENSE](LICENSE)。
