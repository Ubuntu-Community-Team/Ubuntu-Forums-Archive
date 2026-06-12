---
title: "LeagueofLegends Crash in wine."
date: 2010-11-17
forum: Wine
---

### Post by ravensqu on 2010-11-17
Hello, I am currently trying to run League of Legends through wine on lucid x32. Every time I try to run it, I get the exact same error. When running through the terminal, I get this in wine simulating WinXP:

```
brandon@brandon-laptop:~$ cd ~/Downloads && wine LeagueofLegends.exe
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x8
brandon@brandon-laptop:~/Downloads$ 
```In wine simulating Win7, I get this:

```
brandon@brandon-laptop:~$ cd ~/Downloads && wine LeagueofLegends.exe
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x8
err:seh:setup_exception_record nested exception on signal stack in thread 001d eip 7bc725f0 esp 7ffd7c7c stack 0xc92000-0xe90000
brandon@brandon-laptop:~/Downloads$ 
```I have already tried running and installing vcrn2005 through winetricks. I have only seen this problem in one other thread and it is marked solved with no solution given in the thread. Please help me with this problem.

---

