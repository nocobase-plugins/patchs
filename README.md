# patchs 仓库使用说明

本仓库用于存放 [nocobase](https://github.com/nocobase/nocobase) 项目的补丁（patch）文件，帮助用户快速将特定功能或修复集成到自己的 nocobase 代码库中。

---

## 1. patch 文件的用途

patch 文件记录了某个功能或修复相对于主仓库的代码差异。你可以通过 patch 文件将这些更改应用到你本地的 nocobase 仓库，无需手动修改每个文件。

---

## 2. 适用场景
- 想提前体验某些新功能或修复，但官方仓库还未合并。
- 需要在自己项目中集成社区贡献的补丁。
- 方便团队成员同步特定更改。

---

## 3. 操作前准备
1. **Fork 并 Clone nocobase 主仓库**
   ```bash
   git clone git@github.com:你的用户名/nocobase.git
   cd nocobase
   git remote add upstream git@github.com:nocobase/nocobase.git
   git fetch upstream
   ```
2. **建议新建分支操作**
   ```bash
   git checkout -b feature/apply-patch upstream/main
   ```

---

## 4. 应用 patch 文件的详细步骤
1. **下载 patch 文件**
   - 直接在本仓库页面点击 patch 文件，选择 "Raw"，右键另存为本地文件。

2. **在 nocobase 仓库根目录下应用 patch**
   ```bash
   git apply /path/to/patchs/input-add-clearable-config.patch
   # 或
   git apply /path/to/patchs/table-add-zebra-stripes.patch
   ```

3. **检查并提交更改**
   ```bash
   git status
   git add .
   git commit -m "Apply input-add-clearable-config patch"
   ```

4. **推送到你的远程仓库（可选）**
   ```bash
   git push origin feature/apply-patch
   ```

5. **如需发起 PR，可在 GitHub 网页操作**

---

## 5. 常见问题与注意事项
- patch 只能应用到与其生成时一致或相近的 nocobase 版本，否则可能失败。
- 如果 `git apply` 报错，可尝试 `git apply --reject --whitespace=fix patch文件`，手动处理冲突。
- 建议在新分支操作，避免污染主分支。
- patch 只会修改代码，不会自动安装依赖，如有依赖变更请手动执行 `npm install` 或 `yarn`。

---
