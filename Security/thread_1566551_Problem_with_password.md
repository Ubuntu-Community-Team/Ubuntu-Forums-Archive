---
title: "Problem with password"
date: 2010-09-02
forum: Security
---

### Post by Mohannad101 on 2010-09-02
[SIZE=2]Hello all
actually I'm new user in Lunix and I've used Ubuntu lately, my problem is with my current password, I changed it to another one in other language newly but when I turned the computer off then turned it on, it became doesn't accept neither new password nor old, now I cant do update or any other things need password before that, what should I do till solve this problem and I wish it can be solve without reinstall the operation again with my regards, thanks
[/SIZE]

---

### Post by Rubi1200 on 2010-09-02
This guide helps you reset your password:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by ajgreeny on 2010-09-02
I think that link is incorrect.

Here's the real one:  [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Rubi1200 on 2010-09-02
@ ajgreeny

Oops :redface:

You are absolutely right!

I was also posting the instructions for reinstalling GRUB and had the other link open for this; must have forgotten to copy/paste

Thanks for spotting and correcting it.

:)

---

### Post by Mohannad101 on 2010-09-02
thanks very much guys, I did what I read in that link but when I write 1s /home appears to me you entered wrong and things like that then I wrote *sudo passwd* and appeared to me enter unix password I wrote new one then rewrite it again and saw that operation completed successfully after that I chose *resume normal boot *and appears enter to log in, I wrote the new paswrd but it was unacceptable, I repeat the operation again but in the root shell prompt which appears after I choose *Drop to root shell prompt* I find this sentence: *Give root password for maintenance (or type control1-D to continue):_*
and the letters doesn't appears when I write in front of that sentence
I don't know what's wrong>__<[
BTW I use Ubuntu 10.04

---

### Post by ajgreeny on 2010-09-02
> **Mohannad101 said:**
> [SIZE=2]thanks very much guys, I did what I read in that link but when I write 1s /home appears to me you entered wrong and things like that then I wrote *sudo passwd* and appeared to me enter unix password I wrote new one then rewrite it again and saw that operation completed successfully after that I chose *resume normal boot *and appears enter to log in, I wrote the new paswrd but it was unacceptable, I repeat the operation again but in the root shell prompt which appears after I choose *Drop to root shell prompt* I find this sentence: *Give root password for maintenance (or type control1-D to continue):_*[/SIZE]
[SIZE=2]and the letters doesn't appears when I write in front of that sentence[/SIZE]
[SIZE=2]I don't know what's wrong>__<[/SIZE]
[SIZE=2]BTW I use Ubuntu 10.04[/SIZE]

The command is "ls /home" not "1s /home" as you wrote, (lower case L), and it does warn about that possible mistake in the link I gave you.

You should not have used "sudo passwd" but "passwd *user*" with *user* being the username you found in the "ls /home" command.  I am not quite surewhere you are now having tried all those incorrect things, but I think you can still get your user password to work properly by following all the details of that link, but more carefully next time.

I think the reason you are asked for a root password is because using the "sudo passwd" command has made that for you, which is quite un-necessary in ubuntu, which uses "sudo" instead.

---

### Post by philcar on 2010-09-03
> **ajgreeny said:**
> The command is "ls /home" not "1s /home" as you wrote, (lower case L), and it does warn about that possible mistake in the link I gave you.
 
You should not have used "sudo passwd" but "passwd *user*" with *user* being the username you found in the "ls /home" command. I am not quite surewhere you are now having tried all those incorrect things, but I think you can still get your user password to work properly by following all the details of that link, but more carefully next time.
 
I think the reason you are asked for a root password is because using the "sudo passwd" command has made that for you, which is quite un-necessary in ubuntu, which uses "sudo" instead.
 
Hello everybody,
I have the same problem,I entered the ls/home command and received the same reply.

---

### Post by Mohannad101 on 2010-09-03
[SIZE=2]Thanks ajgreeny I appreciate ur help, I wrote sudo passwd because I found is/home doesn't work but it was my mistake because I didn't focus that it lower case of L, anyway these mistake happens with me when I use something new for the first time, now I fixed all that by reinstall Ubuntu again and now everythings are okay
my regards
[/SIZE]

---

### Post by msandoy on 2010-09-03
I just have a short question, have you changed the keyboard layout after installation or after replacing the password the first time? I have some problems with passwords containing special characters, since I usually have two different keyboard layouts installed. All special characters are located in different places. You might come into troubble if you installed something else than a qwerty keyboard after install.

---

