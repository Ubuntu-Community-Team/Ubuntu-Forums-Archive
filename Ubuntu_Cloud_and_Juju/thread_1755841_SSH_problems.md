---
title: "SSH problems"
date: 2011-05-11
forum: Ubuntu Cloud and Juju
---

### Post by Nick_Fennell on 2011-05-11
Just to let you know I'm pretty new to Ubuntu and the forum but can anyone help me please I'm tying to run an instance everything has pretty much gone to plan so far but i can not connect via ssh although i have added the correct permissions via 
      [FONT=Courier New] euca-authorize -P tcp -p 22 -s 0.0.0.0/0 default[/FONT]

but when i come to connect i get a no route to host message. i have done a debug and got this output if its any help 

[FONT=Courier New]OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
Warning: Identity file mykey.priv not accessible: No such file or directory.
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.0.70 [192.168.0.70] port 22.
debug1: connect to address 192.168.0.70 port 22: Connection refused
ssh: connect to host 192.168.0.70 port 22: Connection refused[/FONT]

thank you

---

### Post by Rusty au Lait on 2011-05-12
Where is the file mykey.priv (if you followed the CD install it will be in the ~/.euca subdirectory or in your home directory otherwise)?

Can you ping your instance from the CLC?

Are you using the correct ssh command?
ssh -i ~/.euca/mykey.priv ubuntu@{ip address of instance}

---

### Post by Nick_Fennell on 2011-05-13
with regards to the install i have followed the server guide to the letter but im going to try running this command again see if that works

[FONT=Courier New]if [ ! -e ~/.euca/mykey.priv ]; then
    touch ~/.euca/mykey.priv
    chmod 0600 ~/.euca/mykey.priv
    euca-add-keypair mykey > ~/.euca/mykey.priv
fi[/FONT]

thanks for taking the time to respond.

---

### Post by Rusty au Lait on 2011-05-15
I believe if you try running that piece of bash code nothing will happen. As I see it, you've already created the file mykey.priv in the .euca subdirectory. This test:
> 
if [ ! -e ~/.euca/mykey.priv ]; then

 will fail and the code will not be executed.

---

