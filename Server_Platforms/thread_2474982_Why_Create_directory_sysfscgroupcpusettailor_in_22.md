---
title: "Why Create directory /sys/fs/cgroup/cpuset/tailor in 22.04 no files:cpuset.cpus&#12289;tasks"
date: 2022-05-13
forum: Server Platforms
---

### Post by chen780929 on 2022-05-13
Hey all,

Why Create directory /sys/fs/cgroup/cpuset/tailor in Ubuntu 22.04 LTS no files:cpuset.cpus&#12289;tasks&#12289;cpuset.mems&#65311;But there are these files in 20.04 LST.
[COLOR=#333333][FONT=Arial]Can't do CPU affinity Settings in [/FONT][/COLOR]Ubuntu [COLOR=#333333][FONT=Arial]22.04 LTS without these files.  Is there another way to set CPU affinity in [/FONT][/COLOR]Ubuntu [COLOR=#333333][FONT=Arial]22.04 LTS?[/FONT][/COLOR]
I have an issue where when I go to Ubuntu 22.04 LTS setting cpuset
root@ubuntu:/sys/fs/cgroup/cpuset# mkdir tailor tinker
root@ubuntu:/sys/fs/cgroup/cpuset#ls tailor
cgroup.controllers  cgroup.kill             cgroup.procs            cgroup.threads  cpu.stat
cgroup.events       cgroup.max.depth        cgroup.stat             cgroup.type     io.pressure
cgroup.freeze       cgroup.max.descendants  cgroup.subtree_control  cpu.pressure    memory.pressure

Ubuntu 20.04 LTS  server setting cpuset:
root@ub20:/sys/fs/cgroup/cpuset# mkdir tailor tinker
root@ub20:/sys/fs/cgroup/cpuset# cd tailor/
root@ub20:/sys/fs/cgroup/cpuset/tailor# ls
cgroup.clone_children  cpuset.effective_cpus  cpuset.memory_migrate      cpuset.mems                      tasks
cgroup.procs           cpuset.effective_mems  cpuset.memory_pressure     cpuset.sched_load_balance
cpuset.cpu_exclusive   cpuset.mem_exclusive   cpuset.memory_spread_page  cpuset.sched_relax_domain_level
cpuset.cpus            cpuset.mem_hardwall    cpuset.memory_spread_slab  notify_on_release

---

