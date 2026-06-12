---
title: "Allowing X forwarding in SSH"
date: 2006-04-23
forum: Server Platforms
---

### Post by ebin on 2006-04-23
I am a new linux user so am trying to figure everything out..My ssh server, for some reason will not allow users to get access to X-server. I was wondering if I have to enable it or something. I do not even know how to change the SSH server options. Thanks.

---

### Post by LordHunter317 on 2006-04-23
You need to edit /etc/ssh/sshd_config, enable the appropriate option (it's obvious) and restart sshd via "sudo /etc/init.d/ssh restart"

---

### Post by imagine on 2006-04-23
And the client also has to enable X11 forwarding with the -Y switch or in the .ssh_config.

---

### Post by LordHunter317 on 2006-04-23
I could mistaken as I haven't done it from a terminal in a while, but I'm 99% positive it's -X.

---

### Post by imagine on 2006-04-23
Yes and no.

By using X11Forwarding you allow the machine with the SSH server to access the X server on your client. A person with root privileges on the SSH server machine could use that to try wreaking havoc over your client.


-X is the untrusted and thereby more secure version of -Y, but it's generally slower, some applications don't work and if I don't trust the server, well then I shouldn't connect to it anyway IMHO.
Before version 3.8 of OpenSSH -Y didn't exist and IIRC -X was what now -Y is. There is a nice documentation from HP about all that, but it's 4:00 in the morning here and I cba to search it now : )

---

### Post by LordHunter317 on 2006-04-23
That's not the issue.  You may trust yourself on the server, but if it's a shared machine (e.g., university box) you may not trust the other users.  In which case, you should use -X.

---

### Post by ebin on 2006-04-24
Yes I have done those things, I guess the problem is with something else. I am using CYGWIN to ssh from my windows laptop to Ubuntu box. Everytime I try (with X or Y) I get two different errors: "error in locking authority file /home/ebin/.Xauthority" and "/home/ebin/.Xauthority not writable, changes will be ignored" respectively. I have read fourms about the MIT cookie, but I get similar messages. There is a quick way I KNEW how to genearate a random 32-bit hex key and copy it to the source computer (but now I forget how) anyway that didn't work either. I had someone who knows how to ssh -X, ssh onto his linux box and it worked. Something is wrong with mine. I know this is vauge but if anyone has any ideas I can provide additional information as required. Thanks

---

### Post by tribaal on 2006-04-24
Stupid question (hopefully related): does the server need to be running an X server for this to be feasible?
 
I would like the answer to be "no", but... :rolleyes: 

- trib'

---

