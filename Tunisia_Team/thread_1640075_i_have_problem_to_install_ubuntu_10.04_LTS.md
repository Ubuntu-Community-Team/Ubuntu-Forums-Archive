---
title: "i have problem to install ubuntu 10.04 LTS"
date: 2010-12-07
forum: Tunisia Team
---

### Post by dark of angel on 2010-12-07
HI 
 i have a new laptop [toshiba satellite (C600-02l) "this is what wrotten on this laptop"
i want to install any ubuntu version  itries with 10.04 LTS but after booting list of message shows up
acpci .....with adress 
acpci.....
what i capt is the last message kenel_thread_helper +06....
igoogled but i fond that this hardware seems to be  incompatible with my hardware 
plzz 
 one tell me that i'm wrong and this is the solution....
i really in need

---

### Post by dark of angel on 2010-12-07
i found the solution of installation 
F6 and make option noapci=off 
this for installation 
but  in stated ubuntu a ihave the same problem(same message "thread_helper...")
i become nut 2day
i'l keep u informated

---

### Post by sikander3786 on 2010-12-07
See this.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

And once Ubuntu is installed and you need to make that change permanent, edit /etc/default/grub by,

```
gksudo gedit /etc/default/grub
```

And type your desired parameter in between the quotes in this line.

```
GRUB_CMDLINE_LINUX=""
```

Save and close that file and update Grub by,

```
sudo update-grub
```

But remember, the terminology of those commands is either *acpi=off* or *noapic* or *nolapic*. I haven't heard of *noapci=off*. Make sure you type the correct syntax there.

---

### Post by dark of angel on 2010-12-07
i have already install ubuntu 10.04 
but when i choos it ² the same problem appears
"kernel_thread_helper+0x7/0x10
kernel init +0x0/0xbf
.....
and too many message in the sameway

---

### Post by sikander3786 on 2010-12-07
OK. Highlighting the first entry in Grub menu, press 'e' to edit it, then navigate to the words "quiet & splash" and type your desired parameter following those 2 words. Press Ctrl + X to boot and see if it can boot successully this time.

---

### Post by dark of angel on 2010-12-07
> **sikander3786 said:**
> OK. Highlighting the first entry in Grub menu, press 'e' to edit it, then navigate to the words "quiet & splash" and type your desired parameter following those 2 words. Press Ctrl + X to boot and see if it can boot successully this time.

thank u it's run ubuntu and i applied ur tutoriel with the command "**acpi=off**" but i found that network wire didn't work 
so strange !!!!

---

### Post by sikander3786 on 2010-12-08
You are Welcome. Glad to know that it worked :-)

Regarding the network problem, it requires a new thread under Networking & Wireless sub-forum.

If your installation issue is solved, you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

