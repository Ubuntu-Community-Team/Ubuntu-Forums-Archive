---
title: "create a livecd with dfsbuild"
date: 2008-08-26
forum: Server Platforms
---

### Post by SpaceTeddy on 2008-08-26
I've just searched the forums and found no match when looking for dfsbuild. Also, i am putting this in the server section since i want to make a live-cd from a server installation that has a few modifications. I have my system installed in a VM and it it ready to go.. but i cannot figure out how to use dfsbuild. 

here is the output of what i am getting when i start it:
> root@Master:/etc/dfsbuild# rm /tmp/dfs/ -R && dfsbuild -a i386 -c /etc/dfsbuild/dfs.cfg -w /tmp/dfs
[dfs/INFO] Welcome to dfsbuild.  Image architecture: "i386"
[dfs/INFO] Using working directory /tmp/dfs
[dfs/INFO] Using library directory /usr/lib/dfsbuild
[dfs/INFO] Running.
[dfs/INFO] Mirroring process starting.
[dfs/INFO] Running cdebootstrap for hardy
**E: Unknown suite hardy**
[dfs/CRITICAL] Exception: user error (("cdebootstrap",["-q","-d","hardy","/tmp/dfs/target","http://de.archive.ubuntu.com/ubuntu/"]): exited with code 1)
dfsbuild: user error (("cdebootstrap",["-q","-d","hardy","/tmp/dfs/target","http://de.archive.ubuntu.com/ubuntu/"]): exited with code 1)


the bold is what bugs me most. What am i supposed to put there - what is a suite ? the documentation for dfsbuild is non existent (as far as i could find) and i am pretty much stuck on it. I cannot get it past that state. So does anybody have any idea on how to do this ? Or do i need to use a different tool (already tried bootcdwrite, which throws a few shell errors and then has a fatal abort with an equally useless error message).

Any help would be greatly appreciated...
PS: if you need any info, just ask. I'll gladly supply it

---

### Post by Oldsoldier2003 on 2008-08-27
tagged for help by the Unanswered Posts team. Maybe someone there can give you a hand, if not its a free bump :)

---

### Post by SpaceTeddy on 2008-08-31
thanks for the bump... but i'll do it again :(

is there really nobody out there that has any hint on how to turn a working ubuntu install into a live cd ???

---

### Post by cjssmo on 2008-11-19
I am experienceing the same problem.  There has already been a few bug reported to the debian bts about this with no response from the dev.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=467543](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=467543)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=465944](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=465944)

not much help but at least it has been reported

---

