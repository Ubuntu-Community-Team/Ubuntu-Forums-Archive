---
title: "uninstall usp"
date: 2009-11-10
forum: Ubuntu System Panel
---

### Post by dzon65 on 2009-11-10
I've installed usp but I'm having a problem with it.Every time I close it,the windowborders remain on my desktop only to dissapear after reboot.Now I can't uninstall it.I've downloaded the file to my desktop and when I put this command in (cd ~/Desktop/SVN/ubuntu-system-panel
./usp_update uninstall complete)nothing happens,the file isn't recognized.Anyone an idea?

---

### Post by dzon65 on 2009-11-10
When I try this:
sudo dpkg -r usp,I get this:dpkg: warning: ignoring request to remove usp which isn't installed.
Don't get it,it IS there allright.

---

### Post by Malac on 2009-11-10
Hi dzon65,
Sorry you have had trouble it sounds like you are suffering from a compiz bug which affects usp.
The workaround is here :
[http://ubuntuforums.org/showpost.php?p=8288078&postcount=1068](http://ubuntuforums.org/showpost.php?p=8288078&postcount=1068)

How did you install usp was it from the SVN or by adding it to the apt/synaptic repositories?

---

### Post by dzon65 on 2009-11-11
Well,I installed it with SVN,it wasn't in repos.I tried the solution but the lines are still there.(it's a great tip though)
I have to uninstall this usp,but it's a bit difficult without the wright terminal command,and it's absence in synaptic.Using the ones from SVN doesn't help much (nothing that is).
So,if you happened to have the wright command,I'd be much obliged.

---

### Post by Malac on 2009-11-13
> **dzon65 said:**
> Well,I installed it with SVN,it wasn't in repos.I tried the solution but the lines are still there.(it's a great tip though)
I have to uninstall this usp,but it's a bit difficult without the wright terminal command,and it's absence in synaptic.Using the ones from SVN doesn't help much (nothing that is).
So,if you happened to have the wright command,I'd be much obliged.
Press Alt-F2 and enter:```
gksu nautilus
```Navigate to /usr/lib/python2.4/site-packages/
You can just delete the folder "usp"
Then Navigate to /usr/lib/bonobo/servers and delete the file "usp.server"
To remove your preferences as well navigate to /home/<username> and press Ctrl-H to show hidden files and remove the folder ".usp"
That should be everything.
You should then reboot or logout and back in
Hope this helps.

---

### Post by dzon65 on 2009-11-14
Greetings to the New Mills people.Thanks for the tips.

---

### Post by Malac on 2009-11-14
> **dzon65 said:**
> Greetings to the New Mills people.Thanks for the tips.
 You're Welcome. :)

---

