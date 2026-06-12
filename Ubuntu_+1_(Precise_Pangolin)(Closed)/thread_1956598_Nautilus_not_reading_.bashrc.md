---
title: "Nautilus not reading .bashrc ?"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dikkjo on 2012-04-11
Hello,

i have a strange problem since I've updated to 12.04.

The launchers on my desktop ( mostly java apps ) do not work anymore since some env vars (JAVA_HOME and correct PATH) are missing.

Since I have all my jdk's installed in my home, I define this vars in my ~.bash_aliases which is normally sourced by ~.bashrc.

Since 12.04 this do not work anymore on the graphical desktop for *.desktop files, but if I launch the same program from a terminal I have no problem. I also tried to set "Terminal=true" in the launcher file but still no env vars.

Does anyone know if this a change or a bug with nautilus?

Thanks for your help.

---

### Post by roelforg on 2012-04-11
> **dikkjo said:**
> Hello,
 
i have a strange problem since I've updated to 12.04.
 
The launchers on my desktop ( mostly java apps ) do not work anymore since some env vars (JAVA_HOME and correct PATH) are missing.
 
Since I have all my jdk's installed in my home, I define this vars in my ~.bash_aliases which is normally sourced by ~.bashrc.
 
Since 12.04 this do not work anymore on the graphical desktop for *.desktop files, but if I launch the same program from a terminal I have no problem. I also tried to set "Terminal=true" in the launcher file but still no env vars.
 
Does anyone know if this a change or a bug with nautilus?
 
Thanks for your help.
 
I'm not a 12.04 guy, but why would a file manager read a shell config?

---

### Post by cariboo on 2012-04-11
> **roelforg said:**
> I'm not a 12.04 guy, but why would a file manager read a shell config?

Not very helpful, if you can't answer the question, why post?

---

### Post by snkiz on 2012-04-11
I'm getting it too. nothing in my ~/bin works unless I put in the full path. Sorry no idea how to fix it, other than using the full path to run scripts.

---

### Post by roelforg on 2012-04-11
> **cariboo907 said:**
> Not very helpful, if you can't answer the question, why post?

Cause i'm trying to get a better picture of what he wants.

---

### Post by snkiz on 2012-04-11
.desktop launchers should (and used to.) read bashrc. They are run through the file manager are they not?

---

### Post by roelforg on 2012-04-11
> **snkiz said:**
> .desktop launchers should (and used to.) read bashrc. They are run through the file manager are they not?

No, the desktop env. (gnome+unity/kde/lxde/etc...) parses it and runs it.
If you want to click on it in the file mgr, reassociate the extension with a custom command that goes through bash.
EDIT:
I know why it doesn't (anymore?) read .bashrc:
The filemgr can't rely on a user having bash instead of, for example, csh ot tcsh.

---

### Post by MacUntu on 2012-04-11
Try ~/.profile instead.

---

### Post by snkiz on 2012-04-11
> **roelforg said:**
> No, the desktop env. (gnome+unity/kde/lxde/etc...) parses it and runs it.
If you want to click on it in the file mgr, reassociate the extension with a custom command that goes through bash.

That's doesn't make sense. I used to be able to create desktop launchers that pointed to my ~/bin and the worked. Because I had the env variable in bashrc or profile. I think both actually. One works in the terminal and one one the desktop. Now neither work.

---

### Post by roelforg on 2012-04-11
> **snkiz said:**
> That's doesn't make sense. I used to be able to create desktop launchers that pointed to my ~/bin and the worked. Because I had the env variable in bashrc or profile. I think both actually. One works in the terminal and one one the desktop. Now neither work.

Why not?
And, it's a new version! Stuff changes.

---

### Post by snkiz on 2012-04-11
> **roelforg said:**
> Why not?
And, it's a new version! Stuff changes.

Has something to do with being POSIX compliant I believe. I could be wrong, but every Linux distro I've tried works this way. Except 12.04, now.

---

### Post by dikkjo on 2012-04-12
Hello,

Sorry for my late answer was on a job trip few days. 

> **roelforg said:**
> I'm not a 12.04 guy, but why would a file manager read a shell config?

LOL, should I troll o should I flame? But in a sense you are right, after posting this thread, i turned on my grey matter and remembered that in fact is the login/session manager that should load the user env when launching the X session. I will check for bugs on the subject within greeter or lightdm..

To have a clear view of what I want: my env available under X.
Worked for more then 11 years on every Linux/Unix i used, not working on 12.04. 

Anyway I will try all possible solution with .profile, .bash_profile...and let you know the results. 
I will also check for bugs/changes with greeter or lightdm.

Cheers to all,
d

PS: I found it very hard not to flame you, dear roelforg, you clearly have no clue on the subject, so I am not really interested in your opinions. Also when I read "Associate Extensions" this tell me exactly what kind of guy you are.
Why do you think that I only have 2 posts and 11 years of experience with Linux? I let you imagine if I am more on the n00b side or on the opposite...

---

### Post by roelforg on 2012-04-12
> **dikkjo said:**
> Hello,
 
Sorry for my late answer was on a job trip few days. 
 
 
 
LOL, should I troll o should I flame? But in a sense you are right, after posting this thread, i turned on my grey matter and remembered that in fact is the login/session manager that should load the user env when launching the X session. I will check for bugs on the subject within greeter or lightdm..
 
To have a clear view of what I want: my env available under X.
Worked for more then 11 years on every Linux/Unix i used, not working on 12.04. 
 
Anyway I will try all possible solution with .profile, .bash_profile...and let you know the results. 
I will also check for bugs/changes with greeter or lightdm.
 
Cheers to all,
d
 
PS: I found it very hard not to flame you, dear roelforg, you clearly have no clue on the subject, so I am not really interested in your opinions. Also when I read "Associate Extensions" this tell me exactly what kind of guy you are.
Why do you think that I only have 2 posts and 11 years of experience with Linux? I let you imagine if I am more on the n00b side or on the opposite...
 
I was just curious,
i couldn't think of an reason why the file manager would do this.
I looked it up, turn out that nautilus does have an desktop mgr; seems weired to me.
Maybe they started using a different one for desktop mgmt, one that doesn't read the .profile or has it's own .profile file?
 
EDIT:
You're right, i mostly work in terminals.
But i'm interested in gaining knowledge.
Nobody knows everything.

---

### Post by snkiz on 2012-04-12
> **dikkjo said:**
> Hello,

Sorry for my late answer was on a job trip few days. 



LOL, should I troll o should I flame? But in a sense you are right, after posting this thread, i turned on my grey matter and remembered that in fact is the login/session manager that should load the user env when launching the X session. I will check for bugs on the subject within greeter or lightdm..

To have a clear view of what I want: my env available under X.
Worked for more then 11 years on every Linux/Unix i used, not working on 12.04. 

Anyway I will try all possible solution with .profile, .bash_profile...and let you know the results. 
I will also check for bugs/changes with greeter or lightdm.

Cheers to all,
d

PS: I found it very hard not to flame you, dear roelforg, you clearly have no clue on the subject, so I am not really interested in your opinions. Also when I read "Associate Extensions" this tell me exactly what kind of guy you are.
Why do you think that I only have 2 posts and 11 years of experience with Linux? I let you imagine if I am more on the n00b side or on the opposite...

You have more patience than me I await your response.

---

### Post by dikkjo on 2012-04-12
> **MacUntu said:**
> Try ~/.profile instead.

Thanks man, that work as a charm.

And much more nicer than using .bash_aliases for the job ;)

Cheers to all

---

### Post by roelforg on 2012-04-12
> **snkiz said:**
> Has something to do with being POSIX compliant I believe. I could be wrong, but every Linux distro I've tried works this way. Except 12.04, now.
 
Really?
The standard for the .desktop files (the shortcut) is [http://standards.freedesktop.org/desktop-entry-spec/latest/index.html](http://standards.freedesktop.org/desktop-entry-spec/latest/index.html)
The only possibly related thing is the localisation stuff and that's even a long shot.
 
Sorry, didn't/don't want to sound pedantic, it's just that linux is a posix-compliant by design and it was designed without gui so it seemed like it couldn't be true that posix had anything to do with this.
 
EDIT:
Sorry for posting in a solved thread, my timing for clicking on "quote" and on "post" was between the last post and the marking as solved.

---

