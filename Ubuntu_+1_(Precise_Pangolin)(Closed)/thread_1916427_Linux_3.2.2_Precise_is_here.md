---
title: "Linux 3.2.2 Precise is here"
date: 2012-01-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-01-28
The new linux kernel version 3.2.2 is building for Precise in Launchpad (3.2.0-12.20).

Here:
[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-12.20](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-12.20)> 

linux (3.2.0-12.20) precise; urgency=low    [ Andy Whitcroft ]    * switch to new style rebase marker with bug number    [ Leann Ogasawara ]    * Add CONFIG_GPIO_TWL4030=y for arm[el|hf] to the config enforcer     - LP: [#921934]("https://launchpad.net/bugs/921934")    [ Paolo Pisati ]    * [Config] Switch CONFIG_GPIO_TWL4030=y back on arm[el|hf].     - LP: [#921934]("https://launchpad.net/bugs/921934")    [ Tim Gardner ]    * Rebase to v3.2.2, CONFIG_SND_KCTL_JACK=y   * [Config] Add Hyper-V modules to virtual inclusion list     - LP: [#922063]("https://launchpad.net/bugs/922063")    [ Upstream Kernel Changes ]    * Revert "CHROMIUM: enable CONFIG_SECCOMP_FILTER and     CONFIG_HAVE_SECCOMP_FILTER"   * Revert "CHROMIUM: Fix kref usage"   * Revert "CHROMIUM: Fix seccomp_t compile error"   * Revert "CHROMIUM: seccomp_filter: make inherited filters composable"   * Revert "CHROMIUM: seccomp_filter: inheritance documentation"   * Revert "CHROMIUM: seccomp_filter: allow CAP_SYS_ADMIN management of     execve"   * Revert "CHROMIUM: seccomp_filter: remove "skip" from copy and add drop     helper"   * Revert "CHROMIUM: seccomp_filters: clean up warnings; kref mistake"   * Revert "CHROMIUM: seccomp_filters: guard all ftrace wrapper code"   * Revert "CHROMIUM: seccomp_filter: kill NR_syscall references"   * Revert "CHROMIUM: enable CONFIG_BTREE"   * Revert "CHROMIUM: seccomp_filters: move to btrees"   * Revert "CHROMIUM: arm: select HAVE_SECCOMP_FILTER"   * Revert "CHROMIUM: x86: add HAVE_SECCOMP_FILTER and seccomp_execve"   * Revert "CHROMIUM: seccomp_filter: Document what seccomp_filter is and     how it works."   * Revert "CHROMIUM: seccomp_filter: add process state reporting"   * Revert "CHROMIUM: seccomp_filter: new mode with configurable syscall     filters"   * rebase to v3.2.2     - LP: [#795823]("https://launchpad.net/bugs/795823")     - LP: [#909419]("https://launchpad.net/bugs/909419")     - LP: [#724831]("https://launchpad.net/bugs/724831")  -- Tim Gardner <email address hidden>   Thu, 26 Jan 2012 02:54:56 +0000

---

### Post by xyzzyman on 2012-01-28
I have read back to the LP #'s, and I still can't figure out what exactly those Chromium reverts are for...

---

