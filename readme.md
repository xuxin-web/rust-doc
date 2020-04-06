# Rust入门文档

rust是一门编程语言，我选择这们语言的原因是，高性能、内存安全，有具体的规范，跨平台，如果web assembly能成为事实上的可移动二级制平台的话，前景可期。

## 安装

如果想拥有更好的开发体验，使用官方搭建的脚手架 `rustup`。并在vscode中安装 `rust(lts)`插件。[帮助]("https://www.rust-lang.org/learn/get-started")
```bash
# linux下
curl https://sh.rustup.rs -sSf | sh

# 如不存在curl先安装
sudo apt-get install curl
```
下载缓慢，添加执行以下代码 [帮助]("https://mirrors.tuna.tsinghua.edu.cn/help/rustup/")
```bash
 echo 'export RUSTUP_DIST_SERVER=https://mirrors.tuna.tsinghua.edu.cn/rustup' >> ~/.bash_profile
```

库依赖问题，在 `~/.cargo/config` 中添加以下内容 [帮助]("https://www.lakeui.com/p/5e70f1e41125a")
```
[source.crates-io]
registry = "https://github.com/rust-lang/crates.io-index"
replace-with = 'ustc'
[source.ustc]
registry = "git://mirrors.ustc.edu.cn/crates.io-index"

```

## cargo使用
上述安装正确，可以执行 `cargo` 命令，`cargo` 为rust项目的官方脚手架。

创建新项目
```
cargo new 项目名
```
编译项目（需要先切换到项目目录）
```
cargo build
```
编译分发版本（需要先切换到项目目录）
```
cargo build --release
```
执行项目（需要先切换到项目目录）
```
cargo run 
```
检查项目是否存在错误（需要先切换到项目目录）
```
cargo check 
```
更新依赖版本
```
cargo update
```
安装软件
```
cargo install 软件名
```
显示可用命令
```
cargo help 
```

## 基本概念
1. `src/main.rs` 为项目主入口，其中必须包含 `main` 函数
```rust
fn main{
    // 多行代码
}
```
2. 使用库文件，首先在 `Cargo.toml` 文件中添加所需要的库 [帮助]("https://doc.rust-lang.org/cargo/reference/manifest.html")
```toml
[dependencies]
rand = "0.5.5"

```
3. 在使用库文件的地方添加以下代码
```rust
use std::io; // 标准库
use rand::Rng;  //第三方库
use 库名 as 别名;
```
4. 打印输出使用 `println!`宏
```
println!("这里是输出的内容");
println!("{}表示占位符","我会替代占位符中的内容");
```