---
title: "What's the password to log into an SSH server?"
date: 2011-01-23
forum: Server Platforms
---

### Post by Red Raven on 2011-01-23
I have created a basic ssh server and i haven't done any configuring to it other than to port forward port 22. i am trying to connect to it from a client computer (they are on the same router). i enter the command "SSH <IP of the server>", and it asks me for the password. i have tried "SSH <my user name>@<IP of client>", but it says permission denied. am i doing something wrong? thanks!

---

### Post by tgm4883 on 2011-01-23
> **Red Raven said:**
> I have created a basic ssh server and i haven't done any configuring to it other than to port forward port 22. i am trying to connect to it from a client computer (they are on the same router). i enter the command "SSH <IP of the server>", and it asks me for the password. i have tried "SSH <my user name>@<IP of client>", but it says permission denied. am i doing something wrong? thanks!

```
SSH <USERNAME>@<IP of client>
```

That should work. Make sure that username exists as a user on the server and that you are using that users password

---

### Post by matt_symes on 2011-01-23
Hi

You are trying to log on from the client to the server ?

```
ssh <username_on_server>@<ip adress of server>
```

from the client machine and enter the password of the user on the server.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

It's better to use keys than passwords in the long run.

Kind regards

---

### Post by Red Raven on 2011-01-23
> **matt_symes said:**
> Hi

You are trying to log on from the client to the server ?

```
ssh <username_on_server>@<ip adress of server>
```from the client machine and enter the password of the user on the server.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

It's better to use keys than passwords in the long run.

Kind regards

thanks. this seemed to work, but once i did it it gave me the command line of the server. does this mean i'm connected? how do i tell? also, do i have to keep it open?

thanks!

---

### Post by matt_symes on 2011-01-23
Hi

> does this mean i'm connected?

Yes

> how do i tell? 

if the user name is different on the server than on the client type 

```
whoami
```

or look at the prompt or create a file in the home directory on the server and disconnect and check it's not on the client

```
touch ~/test_file
```

> also, do i have to keep it open?

Have a read of this....

[http://nileshbansal.blogspot.com/2007/02/prevent-timeouts-in-ssh.html](http://nileshbansal.blogspot.com/2007/02/prevent-timeouts-in-ssh.html)

Use ssh in connection with screen attach and detach to keep session going after you disconnect.

Also use keys and secure your ssh server.

Kind regards

---

### Post by Red Raven on 2011-01-23
> **matt_symes said:**
> Hi



Yes



if the user name is different on the server than on the client type 

```
whoami
```or look at the prompt or create a file in the home directory on the server and disconnect and check it's not on the client

```
touch ~/test_file
```

Have a read of this....

[http://nileshbansal.blogspot.com/2007/02/prevent-timeouts-in-ssh.html](http://nileshbansal.blogspot.com/2007/02/prevent-timeouts-in-ssh.html)

Use ssh in connection with screen attach and detach to keep session going after you disconnect.

Also use keys and secure your ssh server.

Kind regards

thanks, but that link says it will only work with version 2, and im running the latest 5.7 i think). will it work with the newest version as well? also, do i have to keep the command line to the server open? and does anyone have a good link on using it as a proxy (IDK if i want forwarding/tunneling using it as an encrypted proxy. whats the difference)?


sorry for all the newbie questions. thanks for putting up with me!

---

### Post by matt_symes on 2011-01-23
Hi

> thanks, but that link says it will only work with version 2, and im running the latest 5.7 i think). 

ssh currently comes in version 1 and 2 based on different protocols. This is different than the complied code version you may be using (which is what is assume you mean by 5.7).

[http://www.dbapool.com/faqs/Q_76.html](http://www.dbapool.com/faqs/Q_76.html)

> also, do i have to keep the command line to the server open? 

Not quite sure what you mean, but if i understand you... 

No. As i said use screen with attach and detach. Attach when you logon and detach when you log off. That way you attach to an existing session each time you ssh into the server.

You can connect to the server via ssh, disconnect and reconnect as many times as you want, but if you want to keep the same session then use screen.

> and does anyone have a good link on using it as a proxy (IDK if i want forwarding/tunneling using it as an encrypted proxy. whats the difference)?

ssh is encrypted by default. What the difference ? Not sure what you mean.

I will look for a good tutorial for you if i can.

Kind regards

---

### Post by Red Raven on 2011-01-23
> **matt_symes said:**
> Hi

 

ssh currently comes in version 1 and 2 based on different protocols. This is different than the complied code version you may be using (which is what is assume you mean by 5.7).

[http://www.dbapool.com/faqs/Q_76.html](http://www.dbapool.com/faqs/Q_76.html)



Not quite sure what you mean, but if i understand you... 

No. As i said use screen with attach and detach. Attach when you logon and detach when you log off. That way you attach to an existing session each time you ssh into the server.

You can connect to the server via ssh, disconnect and reconnect as many times as you want, but if you want to keep the same session then use screen.



ssh is encrypted by default. What the difference ? Not sure what you mean.

I will look for a good tutorial for you if i can.

Kind regards

i'm not sure what you mean by attach screen and all that. (what i meant was once i log in from the terminal with the ssh <user name>@<ip>, and enter that password, can i close that terminal?) i still want to know what you meant with the screen thing though.

and as for the encryption thing, i want to be able to use it like a proaxy so i can get past school firewalls. so do i want to make a tunnel or a proxy?

thanks!

---

### Post by matt_symes on 2011-01-23
Hi

> (what i meant was once i log in from the terminal with the ssh <user name>@<ip>, and enter that password, can i close that terminal?)

Yes you can, but it will kill your connection to your server and next time you want to connect you will have to ssh (ssh user_name@server) into it again. That is standard.

> i'm not sure what you mean by attach screen and all that.
<snip>
i still want to know what you meant with the screen thing though.

screen is a terminal command that allows you to create multiple terminal sessions controlled by a program called screen. It also allows you to attach and detach from the screen program.

So lets give an example. 

You ssh into a server from a client PC. You start a number of tasks that are going to take a while but you need to disconnect the client for some reason. 

If you disconnect the client the tasks running on the server will be killed. Not what you want. 

One way around this is to use screen. You log on to the server from the client and type screen. This will create a screen session. 

You start the tasks in the screen session and from the client you disconnect from the screen session. This keeps running on the server. 

You then close the connection to the server from the client safe in the knowledge that your tasks are still running on the server. 

Later you connect to the server, reattach to the screen session and you can see if your task are still running or have completed.

[http://www.oreillynet.com/linux/cmd/cmd.csp?path=s/screen](http://www.oreillynet.com/linux/cmd/cmd.csp?path=s/screen)

> and as for the encryption thing, i want to be able to use it like a proaxy so i can get past school firewalls. so do i want to make a tunnel or a proxy?

You tunnel through a proxy so you have both. The tunnel is the encrypted data stream and the proxy is where you tunnel it to/through.

I am not so sure if i should be telling you how to circumvent your schools firewall though.

Google is your friend.

Kind regards

---

