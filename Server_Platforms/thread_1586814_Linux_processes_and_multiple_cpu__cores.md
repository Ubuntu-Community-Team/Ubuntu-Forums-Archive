---
title: "Linux processes and multiple cpu / cores"
date: 2010-10-02
forum: Server Platforms
---

### Post by zabuch on 2010-10-02
Hello,

Is there any way that a application that runs as one process (1 pid) will use more than one cpu / core? Or is it only possible if the application forks and creates more processes?

---

### Post by BkkBonanza on 2010-10-02
There are three ways I know that a process may run on more than one core.

1. Fork a sub process
2. Create more than one thread in it's process.
3. The CPU will switch cores from time to time with heavy processes to keep the thermal profile balanced. 

There may be more I'm not familiar with. More about threads [here]("http://en.wikipedia.org/wiki/Thread_%28computer_science%29").

---

