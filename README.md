> 这份源码是一个 git 仓库，按章节分了分支。当前 `main` 是最终完整代码，
> `git checkout ch01` … `git checkout ch09` 可以看每一章当时有哪些文件。
> 早期分支只供对照阅读，里面会有指向后续章节的 import，不保证能直接运行。

# EcomRAG — 电商智能客服 Agent

## 技术栈

FastAPI + LangGraph / LangChain + SQLAlchemy / MySQL + Milvus。

聊天、嵌入、重排三组上游各自直连，没有网关那一层。模型名和地址都在 `.env` 里配
(`CHAT_*` / `EMBED_*` / `RERANK_*` 三组)，换供应商、换模型不用改代码。

## 跑起来

```bash
cp .env.example .env      # 填 CHAT_* / EMBED_* / RERANK_* 三组
docker compose up -d      # MySQL
make seed                 # 灌业务测试数据
make dev                  # 依赖容器 + MCP :8101/:8102 + 应用 :8000
```

浏览器打开 <http://localhost:8000> 就是聊天页。

