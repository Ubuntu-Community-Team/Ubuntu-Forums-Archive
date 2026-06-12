---
title: "Socks5"
date: 2008-06-24
forum: Server Platforms
---

### Post by darkrad on 2008-06-24
Hello,
I just installed socks5-rev26 to my xubuntu.
In order to start it, i need to execute those commands:

```
cd socks5-rev26/bin
./socks5 socks5.conf
"type a password"
```

I wish instead that this is done automatically after boot, and that once a while it checks if socks5 is running, else start it.
I have no clue how to script, so any example would be really appreciated.

Many thanks.

---

### Post by darkrad on 2008-06-28
is it possible i get no reply? is it so hard to do that?

---

### Post by darkrad on 2008-07-06
still waiting for a reply.

---

### Post by darkrad on 2008-07-15
still waiting for a reply

---

### Post by darkrad on 2008-07-16
still waiting for a reply

---

### Post by windependence on 2008-07-16
> **darkrad said:**
> Hello,
I just installed socks5-rev26 to my xubuntu.
In order to start it, i need to execute those commands:

```
cd socks5-rev26/bin
./socks5 socks5.conf
"type a password"
```

I wish instead that this is done automatically after boot, and that once a while it checks if socks5 is running, else start it.
I have no clue how to script, so any example would be really appreciated.

Many thanks.


I don't think the second and third comands are correct. What application are you trying to install and can you post a link to the guide ytou are using for the install?

-Tim

---

### Post by darkrad on 2008-07-16
thanks for the reply. The commands are the right ones since i use them to actually start the application. what i wanted was a script that check if it's running and if not that starts it.

---

### Post by windependence on 2008-07-16
I can't help you if I don't understand what you are doing. That is why no one has answered you.

Is "type a password" a command or a command argument?

-Tim

---

### Post by blazercist on 2008-07-16
he means it asks him for his password,  just type those commands like you have them there in a file, save the file, make it executable with sudo chmod +x filename  and then symlink the file to rc but im not sure what runlevel it would go under.

edit, or if you are using the GUI... you can just make a file with those commands, make the file executable  then sudo cp filename /usr/local/bin/ then you goto system>preferences>session and add a startup with the command = filename

---

### Post by windependence on 2008-07-16
I'm thinking this will not run:

```
./socks5 socks5.conf
```


because the *socks5.conf* is probably not an argument.

-Tim

---

### Post by darkrad on 2008-07-16
> **windependence said:**
> I'm thinking this will not run:

```
./socks5 socks5.conf
```


because the *socks5.conf* is probably not an argument.

-Tim

I already said that it's the way i'm running it manually at the moment. I just need to automate the insert of the password when requested.. i'm trying with "expect" but i can't get it to work..

```
#!/usr/bin/expect -f
spawn /home/ciccio/socks5-rev26/bin/./socks5 socks5.conf.e
expect "key:"
sleep 2
send "somepass\n";
sleep 2
```

if i run it, i get the log:

```
spawn /home/ciccio/socks5-rev26/bin/./socks5 socks5.conf.e
Enter config blowfish key:
```

but then it exits and doesn't run in background..
the behaviour of the program when i start it manually is:
```
ciccio@ubuntu:~/socks5-rev26/bin$ ./socks5 socks5.conf.e 
Enter config blowfish key: 
using default value '0' for use_ssl
using default value '' for ssl_cert
using default value '0' for no_chroot
[BIND - 2530,Wed Jul 16 22:35:02 2008] [Bind] bind to any adr
[-GETIP- - 2530,Wed Jul 16 22:35:02 2008] try to get ip for: www.xxx.com
[-GETIP- - 2530,Wed Jul 16 22:35:02 2008] resolved ip: xxx.xxxx.xxx.xxx
[-SYSTEM- - 2530,Wed Jul 16 22:35:02 2008]  - WARNING: - Could not chroot
[-SYSTEM- - 2530,Wed Jul 16 22:35:02 2008]  - WARNING: - Could not set uid!
[ACCEPT - 2530,Wed Jul 16 22:35:02 2008] [Accept] start
```

any hints?

---

### Post by windependence on 2008-07-16
I understand exactly what you are asking and I was going to help you with the script but I didn't understand what you were doing here. Now, it is a bit clearer. 

Note that there is a few warnings in the startup log. I am assuming you understand what it means that it cannot chroot and set the UID. These are probably non-fatal errors but I am not sure of they are desirable since I still don't know what this thing is supposed to do :) If you can assist me with that, I might be able to help you.

-Tim

---

### Post by darkrad on 2008-07-17
i repeat another time. when i start it manually, the program works fine. so forget the warning and everything else. i just need a script that start the program in the way i start it manually, and that every some time check if it's still running, else it restart... that's all. it's a socks server, but who cares what it does, it doesn't matter the use of the program, what matter is how to start it, and i explained a lot of times yet

To be more precise, when I run the program through a shell, i can't do anything else since it's not ran in background. so when i close the shell or i lost the connection with my server box, socks5 just terminate. I don't run it with & because i wouldn't be able to insert the password.
That's why i want to crontab it and, sometimes, check if it runs...

---

### Post by darkrad on 2008-07-17
ok now i edited like that:

```
#!/usr/local/bin/expect -f
spawn /home/ciccio/socks5-rev26/bin/./socks5 /home/ciccio/socks5-rev26/bin/socks5.conf
expect "*key:*"
sleep 2
send -- "somepassword\r"
send -- "\r"
expect eof
```

and actually it starts... but after like 10 seconds it close it and return to prompt. Why that happen?

---

### Post by windependence on 2008-07-17
Is there a log file for this? That may give you some answers.

-Tim

---

### Post by darkrad on 2008-07-18
No, the program just start correctly (since if i try to connect to the socket server it works) but it exits to the prompt command after few seconds..

---

### Post by koenn on 2008-07-18
> **darkrad said:**
> ok now i edited like that:

```
#!/usr/local/bin/expect -f
spawn /home/ciccio/socks5-rev26/bin/./socks5 /home/ciccio/socks5-rev26/bin/socks5.conf
expect "*key:*"
sleep 2
send -- "somepassword\r"
send -- "\r"
expect eof
```

and actually it starts... but after like 10 seconds it close it and return to prompt. Why that happen?

it probably times out.
try 'interactive' in stead of "expect eof"

on the other hand, of this is supposed to be a server or a daemon, you should be able to run this in background, not interactively, and it wouldn't require a password. I'm thinking your workaround with "expect" is an ugly fix for an deeper configuration problem.

---

### Post by darkrad on 2008-07-18
if i write "interactive" instead of "expect eof" i get this:

```
sock5 is not running
spawn /home/ciccio/socks5-rev26/bin/./socks5 /home/ciccio/socks5-rev26/bin/socks5.conf
Enter config blowfish key: invalid command name "interactive"
    while executing
"interactive"
    (file "/home/ciccio/socks5.expect" line 7)
```

---

### Post by darkrad on 2008-07-18
ok, "interact" is the exact keyword.. Now, if i launch the script, it works but doesn't return to command prompt..there is no way to let it return to command prompt without closing the launched socks5? thanks

---

### Post by koenn on 2008-07-19
> **darkrad said:**
>  Now, if i launch the script, it works but doesn't return to command prompt..there is no way to let it return to command prompt without closing the launched socks5? thanks

Thats what I meant earlier : stuff like socks is meant to be running as a background process, a daemon, a service, .... : it would be extremely unorthodox  if it could only be made to do so by wrapping it in an expect script, so that's probably not the way to do it. 

how about this :
[http://www.yingjenie.com/ying/linux/socks5/part2.html](http://www.yingjenie.com/ying/linux/socks5/part2.html)
(top result for google "socks5 howto")

---

