---
title: "Long shot: push ssh/other remote terminal instead of pull (no ports forwarded)"
date: 2006-06-13
forum: Server Platforms
---

### Post by Chris Tucker on 2006-06-13
Throughout this year i have been working on a LAN server for running sound events and such on a P.A. System in a local school. They wish me to continue my work on the http GUI i have been creating for their ease of use, however i am moving. The school cannot forward any ports to the machine, because they have no control over such things, a higher set of administrations deem port forwards unsecure, for any machine, they use VPNs for their own adminstration needs.

Is there a way i can have the system have a remote terminal for me to work from without needing a port forwarded?
IE: SSH has port 22 (or other) open, and the client "pulls" a connection from it
My requirement: to have the server "push" the connection to a dynamic dns or static IP, and have a special port open on that end...

is this possible or am i kidding myself?

---

### Post by strobhen on 2006-06-14
Yep, you can, and you actually do it with tunneling :-)

Take a look at the R option in the ssh man file, it will allow you to do a "reverse tunnel" from the school's computer to your machine on the internet. The only caveat is that you will need to run the command on the school computer (either have someone type it or make it a cron job).

The syntax is (from the computer in the school):
ssh <your machine's public ip> -R <remote port>:<local IP (127.0.0.1 is best)>:<local port>

so for example

ssh my.machine.com -R 8080:127.0.0.1:22

Probably best to stick to unpriveledged ports on the remote side so you don't have to login as root, etc.

Now, once you have done that, you would connect to the school's machine by typing in:
ssh 127.0.0.1 -p 8080

If you are dealing with a really draconian firewall (and plenty of schools are) you may need to change the ssh ports to 80 or some such.

---

### Post by Chris Tucker on 2006-06-14
Ive been fiddling with this command for hours, cannot get it to work for the life of me... could you help figure out what im missing? Its not the firewall because im not testing it on that server, im testing it on a real one in florida.
server: ssh my.home.ip -R portopenonhomeip:127.0.0.1:22
ssh: connect to host <removed for security> port 22: Connection refused
Nomatter what combinations i use in the port feilds, i cannot get it to connect to the home ip on the port i specify... and its not grabbing it's port from the :22. ive tried my port there aswell.
when i add the -p <myportopened> , it acts like a normal ssh session, and prompts for a password.... 
i want the server to push access to its own ssh server to the home ip, but thats not what this command is doing..

after reading the above post and researching, i understand that tunneling /CAN/ do this, however i cannot find out how. :( any help??

---

### Post by Chris Tucker on 2006-06-14
AHA! i now understand it
for it to work the client running on the server actually has to connect to the home computer... (manual explains it all)

my next dilema is how do i set up a login so that it will run without prompting for a password?
i need to make it so that it runs as a cron job, and will not run multiple simultanious instances.... (could get messy if 100+ clients logged on to my home system ;) )

i would create a special user for this purpose with access to just that single local port, nothing more, to add security for my end. and inevitably the other end too should anyone get ahold of MY passwords to that server, and my dynamic dns provider.

however before i can do either there are those two questions:
How do i make the ssh command not prompt for a login, to use a password from an encrypted file or such?

and how would i format such a line that if there is no ssh session running with such attributes as that dynamic dns address, then the cron job will run, but if it sees an ssh job with that dynamic dns address as part of the command, then the job will not be run?

---

### Post by Glut on 2006-06-14
For the login you will need a public key, which will do away with the need for a password if created without a passphrase (fine if no one can read your private key). use the ssh-keygen utility, it also has a nice man page. The are plenty of how-tos around, do a search.

---

### Post by Chris Tucker on 2006-06-15
thanks! that leaves only one problem: a script to check if the tunnel process is running, and if it isnt, to start one ... i know this is possible with ps aux and sed or grep or anythnig really ...  but i am not too fluent in how to pass / or even get / arguments like true / false from results, and get it all to work

---

### Post by Chris Tucker on 2006-06-20
solved, thanks all that helped, this has so many uses its unbelievable...

heres what i did:
ips and ports and usernames have been removed because this is fairly unsecure, because my dns host i used will change RSA keys from time to time, i had it flush the known_hosts file every 5 minutes, and automatically accept the ssh rsa key on connection, to prevent problems requiring local manipulation to the server w/o forwarded ports.

So heres everything so others can repeat/manipulate what i did to solve their own problems:
First generate a key so the two computers dont need a password for the tunnel, i recommend using a randomly named user for the ssh tunnel with permissions on the tunnel servering computer to, well, nothing! just enough access to bind onto a port. (a regular non-sudoer is good for this, or you can even lock down the account more)

Also, on your SSH tunnel server, open port 22 on its firewall and make sure it has a SSH server installed and running. If your using a port other than 22 for your tunnel server, add -p <porthere> to any line that says ssh  , and -P to any line that says scp (with scp it has to be directly after the scp command, not after the whole line)

on your server without forwarded ports:
```
ssh-keygen -t rsa
```
as the user thats going to be doing the connecting. this user to my knowledge doesnt have to be secured. im using a sudo -i (invoked root) account for my purpose.

then copy this key to the computer hosting the tunnel:
```
scp ~/.ssh/id_rsa.pub remoteusername@remotehost:~/.ssh/authorized_keys2
```

now test it with (from the server with no ports forwarded)
```
ssh -l remoteusername remotehost -o StrictHostKeyChecking=no
```
If it connects without asking for a password or key verification, then you've done it right so far.

Now go set up a dynamic DNS for your ssh tunnel server. I recommend this because its cleaner, and should your IP ever change, its VERY handy.
replace "dnshost" in the following steps with the host you created. 

Now we doublecheck that the host you created works (from the server with no ports forwarded):
```
ssh -l remoteuser dnshost -2 -o StrictHostKeyChecking=no
```
Ive added -2 because ssh version 2 is more secure, this just forces it to use that.

Now find a suitable allowed port like 8080 or something on your ssh tunnel server. There are many ways to do this, one is:
from the server with no ports forwarded:
```
ssh -l remoteuser dnshost  -R 8080:127.0.0.1:22 -2 -o StrictHostKeyChecking=no
```
replace 8080 with some port... port 22 is the port on the server with no ports forwarded that we will be able to connect to
Play around with that untill you DONT get an error about the port.

Now for the scripts to connect...
again, the server with no ports forwarded:
create a file, and when your done, chmod +x it

put inside it:

```

if (ps aux | grep dnshost | grep ssh)
then
        echo "already connected"
else
        echo "no connection found"
        echo "connecting..."
        ssh -l remoteuser dnshost -R 8080:127.0.0.1:22 -2 -N -o StrictHostKeyChecking=no
fi

```

replacing dnshost and remoteuser and 8080 with the stuff youve created

Now save and chmod, and create another, this one will clear the known hosts list every now and then....

```

if (ls ~/.ssh/known_hosts)
then
        echo "cleaning host list"
        rm ~/.ssh/known_hosts
else
        echo "already clean"
fi

```
save and chmod.
now as the user on the server with no ports forwarded that you have done all that, 
```
crontab -e
```
and add:
```

*/2 * * * * /path/to/remoteconnectscript   # check & initialize the remote connection tunnel
*/5 * * * * /path/to/keycleanerscript   # clear the key cache in case the computer at the other end of the tunnel has changed

```
replace the paths with what you want, and the */2 signifies every 2 minutes, */5, every5 minutes, change those if you want, but i keep them low in case a connection times out.
ctrl+o, press enter, and presto

and then from the ssh tunnel server, once you know your server with no ports forwarded is connected, check it all
```
ssh -l serverwithnoportsforwadeduser 127.0.0.1 -p 8080
```
... replacing 8080 with the port you used, and serverwithnoportsforwadeduser with a user you want to use on the server with no ports forwarded.

And if it all works, you have a permanent ssh tunnel!
hope this helps someone, i might write a howto for the forums when i clean up the scripts and the security of this.

Oh yes, and why would there be a server with no ports forwarded?!
in this case its a sound server for a PA system that needs remote monitoring
but any LAN server could use this for a more secure way than having ports open, however the key cleaning bit fooks the security aspect, however the full howto will have that as optional.

---

