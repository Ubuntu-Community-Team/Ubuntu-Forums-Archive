---
title: "topalias: Open-source Python utility: aliases generator from shell history"
date: 2020-11-19
forum: Ubuntu, Linux and OS Chat
---

### Post by csredrat on 2020-11-19
Hi people! &#128039;
I published Open Source utility, it may be useful to someone: [https://github.com/CSRedRat/topalias](https://github.com/CSRedRat/topalias)
The tasks that the program solves:

[LIST]
[*]Parse the ~ / .bash_aliases, ~/.bash_history, ~/.zsh_history files with the history of command execution in the Linux terminal in the Bash/Zsh shell
[*]Suggest short abbreviations (acronyms) for long, long-typed and difficult to remember, but frequently used commands (although you might not even guess about this)
[*]Display some statistics
[*]Process control parameters
[/LIST]
Install and run:

```
pip install topalias
python -m topalias 

```

Any feedback will be welcome :)
If someone is interested project structure, please write. I make actually template for new Python projects with CI/CD (GitHub Actions, GitLab CI, Travis, git pre-commit hooks), lintered "fish" out of the box with documentation and you can run project as package/module/script. Some about project development: [https://github.com/CSRedRat/topalias/wiki/Development](https://github.com/CSRedRat/topalias/wiki/Development)

---

