---
title: "Do I need VMWare server to install VMWare tools"
date: 2008-11-13
forum: Virtualisation
---

### Post by Deadheded on 2008-11-13
I am having trouble finding proper info on VMWare.  I have VMWare player installed on Ubuntu 8.04 64 bit with XP Pro as the guest.  The XP will not load the NIC drivers.  From what I understand I may need VMWare tools.  Do I need to install VMWare server in order to install VMWare tools?

TIA

---

### Post by Deadheded on 2008-11-13
I'm about ready to give up on this.  I installed VMWare server and got it up and running.  I can log in and create VM's without a problem.  Then I want to install the Remote Console add on.  The help section says to go to the 'Console' tab.  The only problem is that I don't have a 'console' tap.  I have 'summary', 'virtual machines', 'tasks', 'event' and 'permissions' but no 'console'.

Does anyone have any ideas?

TIA

---

### Post by dschaller on 2008-11-13
I don't have experience with vmware server, but I have Windows XP Home running fine in vmware player with an Ubuntu 7.10 host. I remember, though, that the default .vmx file that I used did not have the proper NIC reference so I didn't have network access at first either. I had to make a small edit to get it to work.

I don't know if your virtual NIC is failing for the same reason, but look at your .vmx file for the virtual machine and see what the value is on the line ethernet0.virtualDev =

---

### Post by bodhi.zazen on 2008-11-13
What version of VMWare server did you install exactly ?

See also : [https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

---

### Post by Deadheded on 2008-11-13
the latest from vmware  Ver 2.0 I think 64 bit..

I'll keep trying as it is a pain to keep rebooting when I need something from windoze...

---

### Post by bodhi.zazen on 2008-11-13
Ah, so you are asking about the web interface.

On the right you will see a list of virtual machines -> select (clidk on) any one of them.

Then on the left, about 1/3 of the way down is a row of tabs, one of those tabs is labeled console.

[img]http://www.redmountainsw.com/wordpress/wp-content/uploads/vmware-server.png[/img]

---

### Post by Deadheded on 2008-11-13
Now I see my problem, I was using Opera and it does not work with the web interface.  I switched to FF and all seems to show up...

Thanks...

---

