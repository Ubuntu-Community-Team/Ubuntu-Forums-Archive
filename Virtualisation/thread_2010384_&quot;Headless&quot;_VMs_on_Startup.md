---
title: "&quot;Headless&quot; VMs on Startup"
date: 2012-06-25
forum: Virtualisation
---

### Post by Ubun2to on 2012-06-25
I set VirtualBox to launch my Windows XP VM at startup so I can run some applications for work. I used the command:
```
vboxmanage startvm Windows-XP
```
It worked yesterday.
However, it didn't show when I booted up today, so I went to start it manually. It said it was already open. According to the System Monitor, it was "headless", so I had to kill it from there.
So, why does it do that?

---

### Post by Cheesemill on 2012-06-25
Try using:
```
VBoxManage startvm --type gui  Windows-XP
```
To force it to start in GUI mode (although this is the default option so it may not make any difference).

If this still doesn't work then you may also need to prepend a sleep command to make sure that your VM isn't starting before the window manager is fully loaded:
```
sleep 5 && VBoxManage startvm --type gui  Windows-XP
```

---

### Post by Ubun2to on 2012-06-25
> **Cheesemill said:**
> Try using:
```
VBoxManage startvm --type gui  Windows-XP
```
To force it to start in GUI mode (although this is the default option so it may not make any difference).

If this still doesn't work then you may also need to prepend a sleep command to make sure that your VM isn't starting before the window manager is fully loaded:
```
sleep 5 && VBoxManage startvm --type gui  Windows-XP
```

I tried both, and it still won't appear-it remains "headless". Should I adjust sleep from 5 to 10 or 15?
Does it matter what desktop interface you are using?

---

### Post by CharlesA on 2012-06-25
> **Ubun2to said:**
> I tried both, and it still won't appear-it remains "headless". Should I adjust sleep from 5 to 10 or 15?
Does it matter what desktop interface you are using?
It shouldn't matter what DE you are using.

Is the VM just running in the background instead of showing in the VBox manager?

EDIT: I've been running this command to start my VMs headless, it's similar to the one Cheesemill suggested:
vboxmanage startvm vmname --type headless

Try changing the sleep time.

---

### Post by Ubun2to on 2012-06-25
> **CharlesA said:**
> It shouldn't matter what DE you are using.

Is the VM just running in the background instead of showing in the VBox manager?

EDIT: I've been running this command to start my VMs headless, it's similar to the one Cheesemill suggested:
vboxmanage startvm vmname --type headless

Try changing the sleep time.

Did that, and it still is not working.
It's running in the background-I can't bring it up, it just shows up in System Monitor. VirtualBox says it is already on, but provides no way to get to it.
Also, I don't want to start it headless, if you need to know that.

---

### Post by CharlesA on 2012-06-25
If you start it with --type gui, it should launch automatically.

Does it launch if you shut it down and try to launch it that way without rebooting?

---

### Post by Ubun2to on 2012-06-25
> **CharlesA said:**
> If you start it with --type gui, it should launch automatically.

Does it launch if you shut it down and try to launch it that way without rebooting?

Still launches it headless. It shows up as headless in the System Monitor. I do have --type gui in the startup command.

---

### Post by CharlesA on 2012-06-25
Odd.

What happens if you launch it directly from vbox manager?

---

### Post by Ubun2to on 2012-06-25
> **CharlesA said:**
> Odd.

What happens if you launch it directly from vbox manager?

If I press the icon for VirtualBox, I can load it perfectly.
If I press the .vbox virtual machine icon from the VirtualBox VMs folder for my VM, it also loads perfectly. I can also load it via terminal using:
```
VBoxManage startvm Windows-XP
```
Is there a command to load a file via terminal? I've been looking around, but can't find a command to load a specific file.
Also, is there a way to use the cd command and load a file from that specific directory that you switch terminal to in one command? If so, that could make it start VirtualBox correctly.

---

### Post by CharlesA on 2012-06-25
It goes off the name of the virtual machine.

After starting it from the GUI, are you able to run it with VirtualBox --startvm Windows-XP from a terminal?

---

### Post by Ubun2to on 2012-06-25
> **CharlesA said:**
> It goes off the name of the virtual machine.

After starting it from the GUI, are you able to run it with VirtualBox --startvm Windows-XP from a terminal?

Do you mean launch it from the VirtualBox VM list and then launch it from terminal? Or do you mean can I launch it using this command?:
```
VirtualBox --startvm Windows-XP
```
If so, yes, but I get an error:
```
Error opening file for reading: Permission denied
```
And, if I close terminal, it kills the VM.

---

### Post by CharlesA on 2012-06-25
Close virtualbox and then run it from the terminal like this:

```
VirtualBox --startvm Windows-XP &
```

---

### Post by Ubun2to on 2012-06-25
> **CharlesA said:**
> Close virtualbox and then run it from the terminal like this:

```
VirtualBox --startvm Windows-XP &
```
It works, but I get this:
```
me@ubuntu:~$ VirtualBox --startvm Windows-XP &
[1] 5339
me@ubuntu:~$ Error opening file for reading: Permission denied

```
Is it not fast enough to display the Error before the next command entry line comes up?

---

### Post by CharlesA on 2012-06-25
Huh.

Reboot and try it again.

---

### Post by Ubun2to on 2012-06-25
> **CharlesA said:**
> Huh.

Reboot and try it again.
Same thing happened.
Maybe it's an error with using VirtualBox at the beginning of the command rather than VBoxManage (lol-I typed VBoxMange by accident at first).

---

### Post by CharlesA on 2012-06-25
> **Ubun2to said:**
> Same thing happened.
Maybe it's an error with using VirtualBox at the beginning of the command rather than VBoxManage (lol-I typed VBoxMange by accident at first).
Shouldn't matter. I tested it and it worked fine.

Does the VM launch?

---

### Post by Ubun2to on 2012-06-25
> **CharlesA said:**
> Shouldn't matter. I tested it and it worked fine.

Does the VM launch?
Yes, but terminal also gives me this:
```
me@ubuntu:~$ VirtualBox --startvm Windows-XP &
[1] 5339
me@ubuntu:~$ Error opening file for reading: Permission denied


```Edit: So, are we just testing out various commands in terminal to see which ones would work for a startup command, or should I be testing these for the startup commands?
Also, if I log out and log back in to test each command, it runs without a hitch. But, a restart is what seems to make it launch "headless."
Edit 2: I decided to try this command again:
```
VirtualBox --startvm Windows-XP
```It works when I logout and login, but when I reboot, I get this error message:
> Failed to start the virtual machine .I think I'm getting closer to solving this mystery.
Also, these commands also generate this same error message, but they generate it both when I reboot and logoff/logon:
```

VirtualBox --startvm Windows-XP
VirtualBox --startvm Windows-XP &

```
So, it seems that I can get it to work when I relogin, but rebooting makes it fail. I can reboot and login to another account first, and it will work, but not if I reboot and log straight into my account.

---

### Post by CharlesA on 2012-06-25
It must be a bug or something in Vbox. I just tried it on my vmhost and got this:

```
vmuser@Thor:~$ VirtualBox --startvm Orion
Qt WARNING: Unable to load library icui18n "Cannot load library icui18n: (libicui18n.so.48: cannot open shared object file: No such file or directory)" 
Error opening file for reading: Permission denied

```

The Qt warning is cuz I am forwarding X over SSH, as that box is headless.

The VM is running fine tho.

Bug report is here:
[https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1014487](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1014487)

---

### Post by Ubun2to on 2012-06-25
> **CharlesA said:**
> It must be a bug or something in Vbox. I just tried it on my vmhost and got this:

```
vmuser@Thor:~$ VirtualBox --startvm Orion
Qt WARNING: Unable to load library icui18n "Cannot load library icui18n: (libicui18n.so.48: cannot open shared object file: No such file or directory)" 
Error opening file for reading: Permission denied

```The Qt warning is cuz I am forwarding X over SSH, as that box is headless.

The VM is running fine tho.
I'm not sure it's a bug with VBox, as logging out and in will execute most of the commands just fine, but rebooting and logging in fails for all of them. I can login on a different account first and then it will work just fine. Seems like a Ubuntu bug, but VBox might not be able to be automatically executed on the first login session on a computer. I don't know why.

---

### Post by CharlesA on 2012-06-25
> **Ubun2to said:**
> I'm not sure it's a bug with VBox, as logging out and in will execute most of the commands just fine, but rebooting and logging in fails for all of them. I can login on a different account first and then it will work just fine. Seems like a Ubuntu bug, but VBox might not be able to be automatically executed on the first login session on a computer. I don't know why.
*shrugs*

If it is working fine, I'd just leave it for now. Add a comment to the bug report and see what happens.

---

### Post by Ubun2to on 2012-06-26
> **CharlesA said:**
> *shrugs*

If it is working fine, I'd just leave it for now. Add a comment to the bug report and see what happens.
I sent it in to Launchpad. I hope I will get a reply soon.
It only works if I login and log off, or login to another account first. Otherwise, it won't launch.
Should I mark it as solved if I have figured out it is a bug?

---

### Post by CharlesA on 2012-06-26
The odd part is it should launch regardless if you reboot or not.

Do you have the script set to sleep something like 60 seconds so you can make sure you are logged in before it tries to run the command?

---

### Post by Ubun2to on 2012-06-26
> **CharlesA said:**
> The odd part is it should launch regardless if you reboot or not.

Do you have the script set to sleep something like 60 seconds so you can make sure you are logged in before it tries to run the command?

I thought 15 seconds was enough. I have a fairly powerful computer, so I assumed I wouldn't need more than 15 seconds.
Edit: I tried 60 seconds, but it started headless after about 15 seconds, according to the system monitor.

---

### Post by Cheesemill on 2012-06-26
Where exactly are you entering your VM startup command?

---

### Post by Ubun2to on 2012-06-26
> **Cheesemill said:**
> Where exactly are you entering your VM startup command?

I tried all of the ones listed on this thread.

---

### Post by Cheesemill on 2012-06-26
> **Ubun2to said:**
> I tried all of the ones listed on this thread.

Sorry , I think you misunderstood.

I wasn't asking for the command that you tried, I was asking for where you tried entering the command to get it to get it launched on startup.

---

### Post by CharlesA on 2012-06-26
As a sidenote: I have filed a bug report over at virtualbox.org.

[http://www.virtualbox.org/ticket/10707](http://www.virtualbox.org/ticket/10707)

---

### Post by Ubun2to on 2012-06-27
> **Cheesemill said:**
> Sorry , I think you misunderstood.

I wasn't asking for the command that you tried, I was asking for where you tried entering the command to get it to get it launched on startup.

Oh. I used the Startup Applications program. This is the first time it has failed me.

---

### Post by Cheesemill on 2012-06-27
> **Ubun2to said:**
> Oh. I used the Startup Applications program. This is the first time it has failed me.

I was hoping you'd put it somewhere else so I could solve your problem by telling you to put it in 'Startup Applications'.

Oh well :)

---

