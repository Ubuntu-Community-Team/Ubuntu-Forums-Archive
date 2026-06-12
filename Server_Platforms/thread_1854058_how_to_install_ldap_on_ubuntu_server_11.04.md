---
title: "how to install ldap on ubuntu server 11.04"
date: 2011-10-03
forum: Server Platforms
---

### Post by gabikilalala on 2011-10-03
Hello people,

I know i am already getting help in this thread 
[http://ubuntuforums.org/showthread.php?p=11307570#post11307570](http://ubuntuforums.org/showthread.php?p=11307570#post11307570)
but I THINK that it is a very different.Correct me i if i am wrong!Thank you

Well i am already following this guide 
[https://help.ubuntu.com/11.04/serverguide/C/index.html](https://help.ubuntu.com/11.04/serverguide/C/index.html)
but my problem is that after i create 	backend.example.com.ldif file and giving my details i am getting this error!

[HTML]
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=module,cn=config"

adding new entry "olcDatabase=hdb,cn=config"
ldap_add: Other (e.g., implementation specific) error (80)
    additional info: <olcSuffix> namingContext "dc=****,dc=****" already served by a preceding hdb database

[/HTML]

Same thing for file  [B]frontend.example.com.ldif so when i am testing if there is the user john or anyone i get

[/B][HTML]
****@******:~$ ldapsearch -xLLL -b "dc=***,dc=**" uid=**** sn givenName cn
***@***:~$ 
[/HTML]


NOTHING!!!

I have already ignore this and have already continued the guide but when i got to the scripts for adding or removing users,groups etc i got errors.!

Thank you very much in advance.!Tell me what other information give you for helping me.

---

### Post by gabikilalala on 2011-10-04
Hello again, i tried again and continued until i got to the ldap scripts and after this command 
[COLOR=#c20cb9]**sudo**[/COLOR] ldapaddgroup admin

i am getting this error

Error adding group admin to LDAP

.SO???any Help here?

---

### Post by collisionystm on 2011-10-04
Is this a new server install? If so, save yourself alot of headache.

Use Zentyal.

[www.Zentyal.com](www.Zentyal.com)

It is based on Ubuntu 10.04 server, has a web interface.. it is pretty muchh the greatest thing ever.

Enjoy.

---

### Post by collisionystm on 2011-10-04
Is this a new server install? If so, save yourself alot of headache.

Use Zentyal.

[www.Zentyal.com](www.Zentyal.com)

It is based on Ubuntu 10.04 server, has a web interface.. it is pretty muchh the greatest thing ever.

Enjoy.

---

### Post by gabikilalala on 2011-10-04
thank you!
Is it a ldap alternative? Well i want to cobine it with kerberos.Is that possible with this system? Also i have already installed dnsmasq , kerberos , ldap and in the last part for acount and user management i am stack on this please help me!
thanks

---

### Post by collisionystm on 2011-10-04
Zentyal is an all-in-one solution. It can be a firewall, internet gateway, Windows PDC, Ldap Server, email server, DNS, file sharing. In short, its the bomb-diggity.

You would install it to replace what you currently have. I apologize but I am not familiar with any kind of command line ldap. It is far to complicated. I chose to use Zentyal because it just works. There are no tricks.

---

### Post by gabikilalala on 2011-10-04
well i just read about it in their site , but i am trying to get familiar with command line and i i have just started to get used to it. This zentyal is a very very nice solution but is not what i am looking for!Thank you very much.Any ideas about ldap?

---

### Post by gabikilalala on 2011-10-06
Sorry! I have this error:ldap_bind: Invalid credentials (49)

after this command--->ldapadd -x -D cn=admin,cn=config -W -f tmp/cn\=kerberos.ldif

Please i don't see anything wrong.Do you?


Thanks

---

### Post by haqking on 2011-10-07
I am confused, from your other thread i was helping you with you said you wanted a file server and web server you could access from outside ?

now you are setting up LDAP, Kerberos and once again using the example.com information which i already told you is a placeholder where you use your own domain information.

---

### Post by gabikilalala on 2011-10-07
I am following this guide [https://help.ubuntu.com/11.04/serverguide/C/kerberos-ldap.html](https://help.ubuntu.com/11.04/serverguide/C/kerberos-ldap.html)
you had given me. So i am trying to give my server some security but i am not there yet and i started thinking of users in my server and what kind of access should i give them. Is it true? I supposed that i should first install this and later on the basic services am i right?
What do you mean example?No, i think that i am giving my own information. Can you suggest me something?

Thanks

---

### Post by haqking on 2011-10-07
> **gabikilalala said:**
> I am following this guide [https://help.ubuntu.com/11.04/serverguide/C/kerberos-ldap.html](https://help.ubuntu.com/11.04/serverguide/C/kerberos-ldap.html)
you had given me. So i am trying to give my server some security but i am not there yet and i started thinking of users in my server and what kind of access should i give them. Is it true? I supposed that i should first install this and later on the basic services am i right?
What do you mean example?No, i think that i am giving my own information. Can you suggest me something?

Thanks

That guide is a general server guide showing you how to set up various services if you need them.

You dont install and set up and follow every section, only the parts you need.

It is not a step by step from start to finish guide you need to follow.

You dont need 2/3 of that

like was explained to you before example.com like you posted before with "frontend.example.com.ldif so when i am testing if there is the user john or anyone i get" is  placeholder, you enter your own DNS information.

YOU need to start again....LOL

---

### Post by gabikilalala on 2011-10-07
Yes i understood that but if i want to add users in my system is the authentication needed?What is going wrong with me?

---

### Post by haqking on 2011-10-07
> **gabikilalala said:**
> Yes i understood that but if i want to add users in my system is the authentication needed?What is going wrong with me?

so if you understand that why are you still using the example.com entries.

also you dont need all the services.

Install server, setup lamp, setup ssh and setup the users who will use it.

done

---

### Post by gabikilalala on 2011-10-07
I did not put john or something like that. These are old posts.I have found the way to do it and after that i installed succesfully ldap later on succesfully kerberos and now i am trying to give them the chance to collaborate.So i do not have anymore problem with john etc...My problem is my last post.Sorry for confusing you.So can you suggest me something about it?

edit:the example entries do not exist in my system but i have my own information from my dynamic dns service.Why i dont need those services?please explain to me
thanks

---

### Post by haqking on 2011-10-07
> **gabikilalala said:**
> I did not put john or something like that. These are old posts.I have found the way to do it and after that i installed succesfully ldap later on succesfully kerberos and now i am trying to give them the chance to collaborate.So i do not have anymore problem with john etc...My problem is my last post.Sorry for confusing you.So can you suggest me something about it?

edit:the example entries do not exist in my system but i have my own information from my dynamic dns service.Why i dont need those services?please explain to me
thanks

but you dont need LDAP and all the rest, you told me before you wanted a a server (not multiple as you only have one) and you wanted to access files from it and possibly use it as a web server ?

---

### Post by haqking on 2011-10-07
> **gabikilalala said:**
> I did not put john or something like that. These are old posts.I have found the way to do it and after that i installed succesfully ldap later on succesfully kerberos and now i am trying to give them the chance to collaborate.So i do not have anymore problem with john etc...My problem is my last post.Sorry for confusing you.So can you suggest me something about it?

edit:the example entries do not exist in my system but i have my own information from my dynamic dns service.Why i dont need those services?please explain to me
thanks

so now your using your dyndns information which you got from dyndns.org for tracking your changing WAN IP as your DNS information for your LAN ?

---

### Post by gabikilalala on 2011-10-07
Ok but when users from the internet reach my server do not i need authentication and a stop to them,a limit or something?All this staff isnt needed?
Thanks

Yes is that wrong?I have set the domain of my lan with the domain a user can reach me over the internet.Is that wrong?To have the same name?What should i do?(the service i use is no-ip.com)

---

### Post by haqking on 2011-10-07
> **gabikilalala said:**
> Ok but when users from the internet reach my server do not i need authentication and a stop to them,a limit or something?All this staff isnt needed?
Thanks

what users ? how many ?

what are they doing when they reach your server ? 

do you mean using ssh ? or just visiting your website ?

---

### Post by gabikilalala on 2011-10-07
Well i do not how to make a website yet.This is my next step.What i want is to have ftp server and ssh server,mail server or something to host my own email address share directories whith other computers and give some users around ten or more to have theis own storage on my hard drive and share with me files.
Thats all.Maybe i forget something.

Edit : Yes i mean and ssh,and all this staff i told you.thanks

---

### Post by haqking on 2011-10-07
> **gabikilalala said:**
> Well i do not how to make a website yet.This is my next step.What i want is to have ftp server and ssh server,mail server or something to host my own email address share directories whith other computers and give some users around ten or more to have theis own storage on my hard drive and share with me files.
Thats all.Maybe i forget something.

Edit : Yes i mean and ssh,and all this staff i told you.thanks

create your users and then they:

ssh username@ipaddress

thats it, authentication is carried with keys.

---

### Post by gabikilalala on 2011-10-07
So ldap and kerberos?No?Why?Is this going to be a thing that i do not need?So from curiosity Why i cannot do this configuration?what am i doing wrong?
Thank you

---

### Post by haqking on 2011-10-07
> **gabikilalala said:**
> So ldap and kerberos?No?Why?Is this going to be a thing that i do not need?So from curiosity Why i cannot do this configuration?what am i doing wrong?
Thank you

do you have Active Directory ?

---

### Post by gabikilalala on 2011-10-07
well if i am honest and tell you that i do not know what are you talking about will you help me to understand or will you laugh with me?:p
Well if you want help me a little bit more.
Thanks!

---

### Post by haqking on 2011-10-07
> **gabikilalala said:**
> well if i am honest and tell you that i do not know what are you talking about will you help me to understand or will you laugh with me?:p
Well if you want help me a little bit more.
Thanks!

LOL this is why it is difficult helping you at the moment as you dont know yourself what you have or need ;-)

If you dont have Active Directory (windows network) then you dont need LDAP and Kerberos at this stage.

You are following that guide step by step and you dont need to as each section is a different service based on what you need if you need it.

Like i said before you need a basic server installed, configure a static IP for your LAN, then install ssh, setup a static WAN IP or use dynamic dns from the link i provided before so your reach your router WAN interface from across the internet.  Have your router forward port 22 requests from the WAN to the server IP address.

make sure you can SSH to your server from outside and then come back and we can work on each service as you need it.

---

### Post by gabikilalala on 2011-10-07
We could be very good friends|haha;)
Thanks for your help..I am going to remove the services but i have to ask where did you learn all this staff?So i can go learn for my self.

I have a question: I dont have anything installed on my system only apache and openssh server so when i am trying to reach my no-ip.com domain the router sends me to the router ip.I have forwarded ports 80,22,21.in the port 22,21 i have to have installed ftp and ssh right?

---

### Post by haqking on 2011-10-07
> **gabikilalala said:**
> We could be very good friends|haha;)
Thanks for your help..I am going to remove the services but i have to ask where did you learn all this staff?So i can go learn for my self.

I have a question: I dont have anything installed on my system only apache and openssh server so when i am trying to reach my no-ip.com domain the router sends me to the router ip.I have forwarded ports 80,22,21.in the port 22,21 i have to have installed ftp and ssh right?

ok first of all dont use FTP as it is insecure.

use SFTP across your SSH connection once it is established.

your ssh to your WAN IP or Dyndns domain name, this sends you to your router which is connected to the internet.  Your router then needs to be setup to port forward the incoming requests so if it is SSH then port 22 needs to be setup to be forwarded to your server IP address. and same for additional ports.

---

### Post by gabikilalala on 2011-10-07
Ok.But i have already set up my router to forward the port 80 to my server's ip.I think it is easy right?But when i try with my domain name it sends me to the router.When i am trying with my ip it gets me to the it works message of apache!
So?

---

### Post by haqking on 2011-10-07
> **gabikilalala said:**
> Ok.But i have already set up my router to forward the port 80 to my server's ip.I think it is easy right?But when i try with my domain name it sends me to the router.When i am trying with my ip it gets me to the it works message of apache!
So?

you cant do any of this from within your network as most routers do not allow loopback due to NAT functionality.

So you need to test this from outside your network.

---

### Post by gabikilalala on 2011-10-07
Ok, i will try this and i will come back sometime asking you again.thanks dude

---

### Post by CharlesA on 2011-10-07
You can see if it's working by using something such as canyouseeme.org to see if that service can be seen from the internet.

---

### Post by haqking on 2011-10-07
> **CharlesA said:**
> You can see if it's working by using something such as canyouseeme.org to see if that service can be seen from the internet.

yes good idea, forgot about that.

One of the main problems here is that the OP doesnt know what he has or wants (by his own admission) and setup the server following the server setup guide [https://help.ubuntu.com/11.04/serverguide/C/](https://help.ubuntu.com/11.04/serverguide/C/) step by step letter for letter, so has installed everything from beginning to end instead of choosing the services needed ;-)

---

### Post by CharlesA on 2011-10-07
> **haqking said:**
> 
One of the main problems here is that the OP doesnt know what he has or wants (by his own admission) and setup the server following the server setup guide [https://help.ubuntu.com/11.04/serverguide/C/](https://help.ubuntu.com/11.04/serverguide/C/) step by step letter for letter, so has installed everything from beginning to end instead of choosing the services needed ;-)

Been there, done that.. broke ***a ton*** of things and got so confused that I just ended up wiping the drive and starting small - file server at the start and now file/ssh/vm host/web server.

;)

Always have backups too.

Also: I have learned that having a VM to 'play around with' is quite handy.. snapshots are pure win.

---

### Post by haqking on 2011-10-07
> **CharlesA said:**
> Been there, done that.. broke ***a ton*** of things and got so confused that I just ended up wiping the drive and starting small - file server at the start and now file/ssh/vm host/web server.

;)

Always have backups too.

Also: I have learned that having a VM to 'play around with' is quite handy.. snapshots are pure win.

Indeed, before i try anything i am unsure of its in a VM, clones and snapshots save the day and my host in the long run ;-)

why people wipe there machines install something new then ask how to go back to old cos they dont like the new i dont know....but its all an experience i guess.

I remember 10 years ago i was using system commander to have multiple boots and a ghost boot disk to back up my installs before trying something.

Thank god for true virtualisation nowadays though.

---

### Post by CharlesA on 2011-10-07
> **haqking said:**
> Indeed, before i try anything i am unsure of its in a VM, clones and snapshots save the day and my host in the long run ;-)

Definitely. I've done tests on a VM that has totally borked it but fixing the problem is just a snapshot away. ;)

Of course testing on a VM doesn't mean you don't have to test on a physical box either, but it makes it easier to get the initial set up done.

---

