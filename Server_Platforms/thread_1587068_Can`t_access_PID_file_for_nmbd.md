---
title: "Can`t access PID file for nmbd"
date: 2010-10-02
forum: Server Platforms
---

### Post by jaynpc on 2010-10-02
I am having this problem, that says in the boot up ~Could not access PID file for nmbd~/ I have been told to delete splash file. But i don`t know how to do so. And is it really the solution, deleting this file?!

---

### Post by coffee412 on 2010-10-02
> **jaynpc said:**
> I am having this problem, that says in the boot up ~Could not access PID file for nmbd~/ I have been told to delete splash file. But i don`t know how to do so. And is it really the solution, deleting this file?!

Depending on the actual error message, It could mean that the last time nmbd did run it failed to delete the *.pid file. Therefore it will not start again because it cannot overwrite the stale *.pid file. So, You can look for the file (sudo locate *.pid |more) and delete it (rm -f  filename.pid). 

Each process on linux has a pid file to communicate the process number and other info. Its kinda like a place holder if you will for the process. If the process quits the kernel is suppose to delete the pid file. Sometimes things crash and leave the file behind. Then you cannot start the process until the file is deleted.

Did that even remotely help?

:)

---

### Post by jaynpc on 2010-10-02
> **coffee412 said:**
> Depending on the actual error message, It could mean that the last time nmbd did run it failed to delete the *.pid file. Therefore it will not start again because it cannot overwrite the stale *.pid file. So, You can look for the file (sudo locate *.pid |more) and delete it (rm -f  filename.pid). 

Each process on linux has a pid file to communicate the process number and other info. Its kinda like a place holder if you will for the process. If the process quits the kernel is suppose to delete the pid file. Sometimes things crash and leave the file behind. Then you cannot start the process until the file is deleted.

Did that even remotely help?

:)

(50% noob here) So, I understood the thing about the pid file, but i still can`t figure how to make it work, I guess i didn`t explain it right so let me put in another words.

I can`t access linux, it goes until the page where it asks for the password to access and it appears that msg of PID file over and over again and never enters linux. Can i fix this in another way?

---

### Post by coffee412 on 2010-10-02
> **jaynpc said:**
> (50% noob here) So, I understood the thing about the pid file, but i still can`t figure how to make it work, I guess i didn`t explain it right so let me put in another words.

I can`t access linux, it goes until the page where it asks for the password to access and it appears that msg of PID file over and over again and never enters linux. Can i fix this in another way?

The way I would fix it is to boot from the cd and change your boot options and boot to single user mode. 

> [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Then I would tell nmdb not to start on startup. 

> chkconfig nmbd offIf nmbd doesnt work then try nmb.

Then reboot, But keep in mind you still need to fix your origional problem. Find the pid file and delete it.


*** I understand all this might be new to you. But If you just reinstall you will not learn anything. That would be a tragic loss. Google "Ubuntu shutdown nmb" or something similar and do a little investigating and you will learn ALOT. Linux is not hard to understand. The thing is, The more you understand, The more fun it becomes.

---

