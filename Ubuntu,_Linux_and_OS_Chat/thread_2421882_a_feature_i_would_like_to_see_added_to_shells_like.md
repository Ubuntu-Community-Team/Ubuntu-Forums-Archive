---
title: "a feature i would like to see added to shells like bash"
date: 2019-06-28
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-06-28
a feature i would like to see added to shells like bash is the ability to set a different umask value for directories vs. regular files.  i want to use [FONT=courier new]umask 0022[/FONT] for directories but use [FONT=courier new]umask 0222[/FONT] for regular files.

---

### Post by kpatz on 2019-06-28
You can use mkdir -m <mode> to create directories with specific permissions.  For example, **mkdir -m 0755 mydir**.

To make this the default, create an alias: **alias mkdir='mkdir -m 0755'**  You can add this to your ~/.bashrc or ~/.bash_aliases file to make it permanent.

Now anytime you create a directory with mkdir from your shell it will be created with mode 0755.

---

