# UE Texture Change Skill

用于 Codex 的 UE 效果图材质与光影编辑 skill，名称为 `ue-material-lookdev`。

## 工作流程

1. 从用户提供的参考图或 Pinterest 收藏板学习视觉偏好。
2. 基于 UE 主渲染图、Base Color、Normal 等生成区域覆盖图，等待确认。
3. 每轮生成 **1 张 texture**，根据反馈迭代，等待确认。
4. 应用确认的素材，制作效果图预览并对照原图检查几何。

已确认且未变化的选区、素材无需重复确认。偏好与项目记录本地保存，减少重复分析。

## 安装与调用

将本仓库内容放到 Codex 的个人 skills 目录下的 `ue-material-lookdev` 文件夹，例如 `~/.codex/skills/ue-material-lookdev/`。需保留根目录 `SKILL.md` 和引用文件。

调用示例：

> $ue-material-lookdev 根据这组 UE 主图、Base Color 和 Normal，把柱体投影改为花海。先确认选区，每次只生成一张 texture。

首次使用会将 `preferences.example.md` 复制为本地 `preferences.md`；该文件已被 Git 忽略。不要上传个人收藏记录、项目图片、凭据或绝对路径。

## 能力与限制

- 需要可用的图像生成/编辑能力；使用 Codex 内置工具时遵循 imagegen skill。需要确定性图像处理能力才能生成不重绘空间的覆盖图。
- 默认进行普通图像编辑预览，**不要求 ControlNet 或 ComfyUI**。
- 选区展示不等于硬遮罩；普通编辑不能保证原图尺寸、轮廓与镜面反射完全一致。失败结果必须标注，不能冒充合格成图。
- `references/structure-control.md` 是可选、尚未实测的结构控制设计规范，不包含可运行的节点工作流，不代表已经部署 ControlNet。
- 已完成文本与引用检查；尚未验证跨环境完整执行流程。

## 文件

- `SKILL.md`：执行规则。
- `preferences.example.md`：无私人数据的偏好模板。
- `references/structure-control.md`：可选的结构控制规范。
