---
title: "world community grid - BOINC - command line"
date: 2008-12-19
forum: The Cafe
---

### Post by bonfire89 on 2008-12-19
has anyone got World Community Grid and BOINC to work from the command line? I haven't got passed 


apt-get install boinc-manager boinc-client

anyone have any tutorials, or documentation?

I looked at the the list of commands in the man page for boinccmd but that doesn't help when you don't know which commands you need to run.

any tutorials?



thanks

---

### Post by oldos2er on 2008-12-19
After you've installed them, run boinc-manager to setup options from the client.

---

### Post by bonfire89 on 2008-12-20
hmmm

after a bit more fiddling I by a stroke of luck typed in

```
boinc --attach_project www.worldcommunitygrid.org 3e5b512f7c56ff74d834dv1c4a82d396 --daemon --no_gui_rpc

```

3e5b512f7c56ff74d834dv1c4a82d396 being my make key found in my user profile

next, is to figure out how to run that on boot up.. but that is a general linux question.. One I will find the answer to later.

---

