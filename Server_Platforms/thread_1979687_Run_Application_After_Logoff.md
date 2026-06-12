---
title: "Run Application After Logoff"
date: 2012-05-13
forum: Server Platforms
---

### Post by Quick99 on 2012-05-13
I have a Minecraft server running on Ubuntu Server. I want to be able to start and manage the server through my SSH connection. I have tried nohup and it works, but I can't find a way to "un-nohup" the program. I need to be able to give the Minecraft Server input. Is nohup the proper thing to use here or is there something else that works better?

Would the standard practice be to run it as a daemon or something? I am a total linux newb, so I don't really know what that means, but if you can just tell me the name of what to do, I am more than happy to Google it and figure it out myself.

Thanks,
Grant

---

### Post by Tylerjd on 2012-05-14
One word: SCREEN

Screen is a great program for running programs in the background. I run a Minecraft server as well, and this is what I do.

First go ahead and get it (sudo apt-get install screen)

Open terminal, type screen, then enter twice.

It will open what looks like a blank bash session. From their run your minecraft jar (however you please, whether through as script or the java command)

Then when it is all done, on your keyboard hit Ctrl-A-D to "disconnect" from the screen session. The minecraft server will continue to run in the background. You can then login from SSH or a local session, type screen -r to "reattach", and you are back at the Minecraft prompt. Rinse and repeat. If you need to close the Minecraft server and kill the screen session, you can type stop in the Minecraft prompt to stop the minecraft server, then exit at the bash prompt to exit the screen session.

---

### Post by Quick99 on 2012-05-14
Thanks, I appreciate your help!

---

