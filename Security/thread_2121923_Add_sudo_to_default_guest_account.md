---
title: "Add sudo to default guest account"
date: 2013-03-03
forum: Security
---

### Post by WhiteHatGuy on 2013-03-03
Hi

I am trying to add sudo to default guest account

Some one said to follow this process, but I am noob with usermod, and I am very confuse on this one. I dont know where to start.

[COLOR=#333333][FONT=Ubuntu Beta]You could use sudo and the [/FONT][/COLOR]usermod[COLOR=#333333][FONT=Ubuntu Beta] command from an account that [/FONT][/COLOR]*does*[COLOR=#333333][FONT=Ubuntu Beta] have sudo access to add the[/FONT][/COLOR]adm[COLOR=#333333][FONT=Ubuntu Beta] group (for 12.04) to the account. Don't forget to use the [/FONT][/COLOR]-a[COLOR=#333333][FONT=Ubuntu Beta] option to add the group rather than replacing the group list.

I try this comands in terminal:

id tom      

And it sais. 

[/FONT][/COLOR]uid=1000(tom) gid=1000(tom) groups=1000(tom),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),106(lpadmin),117(sambashare)

I am trying id command but with guest account, but sais account do not exist

id guest (account do not exist) I dont know wich is the name that Ubuntu refers to that account

I am lost on this one. Can some one can go on high detail about what is the correct command I need to put
What command I need to put in the terminal in order to do this? I am getting the felling thats is not even a long command. And it must be so simple but as a noob I just cant see it.

Thanks

---

### Post by QIII on 2013-03-03
May I ask first why you would want to give a guest run of the house?  Do you plan to limit the super user authority of the guest account to specific things?

---

### Post by WhiteHatGuy on 2013-03-03
I need to run openvpn and use a vpn connection. But in order to connect it needs administrator rights, it needs sudo. I know that there is a way of hardening openvpn and run it without administrators rights. But thast guide is even more dificult for me cause is obviously made for experience users.

---

### Post by duke.tim on 2013-03-03
This sounds like a dangerous idea.

---

### Post by WhiteHatGuy on 2013-03-03
> **duke.tim said:**
> This sounds like a dangerous idea.


Why dangerous?

---

### Post by duke.tim on 2013-03-03
I say dangerous assuming that by guest you do not mean restricted user account, but an account that would be used by guests.

By giving a guest account the ability to become the Super User, it makes it a LOT easier for someone to break into your system.
They become the administrator and can do anything on your system.

Like Qlll said:
> **QIII said:**
> May I ask first why you would want to give a guest run of the house?  Do you plan to limit the super user authority of the guest account to specific things?

My advice is take the time to understand the more advanced method, you can find information about editing/adding a user to the sudoers file here:
[http://www.garron.me/linux/visudo-command-sudoers-file-sudo-default-editor.html](http://www.garron.me/linux/visudo-command-sudoers-file-sudo-default-editor.html)

And this has an example to add the ability to sudo to a user
[http://askubuntu.com/questions/7477/how-can-i-add-a-new-user-as-sudoer-using-the-command-line](http://askubuntu.com/questions/7477/how-can-i-add-a-new-user-as-sudoer-using-the-command-line)

---

### Post by WhiteHatGuy on 2013-03-03
> **duke.tim said:**
> I say dangerous assuming that by guest you do not mean restricted user account, but an account that would be used by guests.

By giving a guest account the ability to become the Super User, it makes it a LOT easier for someone to break into your system.
They become the administrator and can do anything on your system.

Like Qlll said:


My advice is take the time to understand the more advanced method, you can find information about editing/adding a user to the sudoers file here:
[http://www.garron.me/linux/visudo-command-sudoers-file-sudo-default-editor.html](http://www.garron.me/linux/visudo-command-sudoers-file-sudo-default-editor.html)

And this has an example to add the ability to sudo to a user
[http://askubuntu.com/questions/7477/how-can-i-add-a-new-user-as-sudoer-using-the-command-line](http://askubuntu.com/questions/7477/how-can-i-add-a-new-user-as-sudoer-using-the-command-line)






Ok I see, but actually when I say guest account, I am refering to the one that have by default ubuntu, the one that comes protected with an apparmor profile and that erases anything you do everytime you log in.

---

### Post by lou21 on 2013-03-08
> **WhiteHatGuy said:**
> Ok I see, but actually when I say guest account, I am refering to the one that have by default ubuntu, the one that comes protected with an apparmor profile and that erases anything you do everytime you log in.  Surely if the guest can type "sudo su -" and then get a root prompt they can then install anything and change anything... Including disabling apparmor.

---

### Post by cariboo on 2013-03-08
> **lou21 said:**
> Surely if the guest can type "sudo su -" and then get a root prompt they can then install anything and change anything... Including disabling apparmor.

A user needs to be in the sudo group in order to use it, the quest account is not a member of the sudo group, and can't be made a member.

---

