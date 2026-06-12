---
title: "Idea for extra security layer on Linux"
date: 2005-03-29
forum: Server Platforms
---

### Post by UbuWu on 2005-03-29
As more and more people are switching to linux, I think there should be added some extra security mechanisms to linux. The following is what came to my mind: On linux it is now all or (almost) nothing: or you are a normal user, or you are root or sudoing. That means that when I need to install some software, not an uncommon thing, at the same time I have the chance to ruin my whole system. I thought maybe there can be something in between that allows people to install new software (and maybe removing it as well), but doesn't allow them to do the most harmfull things like rm -rf /*... or doing things to the kernel. 

Maybe this is a stupid idea, maybe it is brilliant, I don't know. Maybe there is already something like it... Would like to here some comments from the people that know more about it.

---

### Post by bored2k on 2005-03-29
[QUOTE=UbuWu]As more and more people are switching to linux, I think there should be added some extra security mechanisms to linux. The following is what came to my mind: On linux it is now all or (almost) nothing: or you are a normal user, or you are root or sudoing. That means that when I need to install some software, not an uncommon thing, at the same time I have the chance to ruin my whole system. I thought maybe there can be something in between that allows people to install new software (and maybe removing it as well), but doesn't allow them to do the most harmfull things like rm -rf /*... or doing things to the kernel. 

Maybe this is a stupid idea, maybe it is brilliant, I don't know. Maybe there is already something like it... Would like to here some comments from the people that know more about it.[/QUOTE]
 That's what sudo is all about . Allow regular uses desired super user commands assigned by the administrator. If the admin allows bored to sudo mount a drive, but not to sudo rm -rf /*, there is no way this side of Neverland I'm going to be able to do such act .

This might be helpful:
> sudo man sudo
DESCRIPTION
       sudo allows a permitted user to execute a command as the superuser or
       another user, as specified in the sudoers file.  
--
On top of it, regular users should not be able to install or install something with system wide changes [on the regular scenario], that why we have things like the new stable autopackage, .bin installers and source packages. 

*drops two cents*

---

### Post by UbuWu on 2005-03-29
Ok, then it probably was a stupid suggestion. I read the sudo manpage, but could you explain me how I could get it done then? E.g. when I want to do the following: allow my father (username peter) to install / remove software using synaptic and the updatenotifier but not to do anything else with sudo.

---

### Post by UbuWu on 2005-03-29
man sudoers did the trick!

---

### Post by bored2k on 2005-03-29
[QUOTE=UbuWu]man sudoers did the trick![/QUOTE]
 Good to know.

---

