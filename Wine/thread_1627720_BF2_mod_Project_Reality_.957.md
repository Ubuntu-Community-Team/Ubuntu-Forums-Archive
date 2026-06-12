---
title: "BF2 mod Project Reality .957"
date: 2010-11-21
forum: Wine
---

### Post by masterskop on 2010-11-21
Hi,

Has anyone been able to play the BF2 mod Project Reality .957 through wine?  I have trying to figure out how to get this to just startup.  BF2 and BF2 special forces work really well, but not the PR .957 mod.

---

### Post by s1mmel on 2011-06-29
> **masterskop said:**
> Hi,

Has anyone been able to play the BF2 mod Project Reality .957 through wine?  I have trying to figure out how to get this to just startup.  BF2 and BF2 special forces work really well, but not the PR .957 mod.

Well, I'm trying but it uses .NET stuff. So you need to start it with mono. I did that, but PR seems to have problems getting some config files. I don't know really why, but my guess would be the space between Battlefield[space]2 in the directory it sets up. Still working on it, but I don't have much hope that it'll run.

---

### Post by masterskop on 2011-07-01
[QUOTE=s1mmel;10996553]Well, I'm trying but it uses .NET stuff. So you need to start it with mono. I did that, but PR seems to have problems getting some config files. I don't know really why, but my guess would be the space between Battlefield[space]2 in the directory it sets up. Still working on it, but I don't have much hope that it'll run.[/QUOTE

s1mmel,

How did you get PR2 to start with mono?  I quit using mono b/c I did not know how to use the commands correctly.  Perhaps we could work together on this.  I'll probably have to delete mono out of my system and start over.  I would much appreciate a detailed step by step on setting up mono on your system.  Then we could figure out the config files.

---

### Post by s1mmel on 2011-07-07
> **masterskop said:**
> 
How did you get PR2 to start with mono?  I quit using mono b/c I did not know how to use the commands correctly.  Perhaps we could work together on this.  I'll probably have to delete mono out of my system and start over.  I would much appreciate a detailed step by step on setting up mono on your system.  Then we could figure out the config files.

I just installed mono and didn't temper with any config file, but instead of starting BF2 with wine I started the pr.exe with the mono command like so

```

mono /dir/to/pr/pr.exe

```

That's about it. Problem is though, that PR has some problems with directories or files in directories (it looks up files in the wrong places). Also I don't think that pr.exe can start bf2.exe (through wine). 

Well, give it a try....

---

