---
title: "shell script to control a shell script?"
date: 2019-11-09
forum: Server Platforms
---

### Post by youmustnot on 2019-11-09
Hello,
I'm still new with linux but, I have a server with ubuntu 18.04. 

I've installed and gotten running a rust game server using [LGSM]("https://linuxgsm.com/lgsm/rustserver/") 
I control the server with commands like:  ./rustserver restart, ./rustserver wipe.

During a wipe and/or an update i have to do somethings manually that i'd like to automate. 
But I cant get my script to control the other script, I'd be grateful of some pointers or even a good link to read up on this type of thing.

heres my script:
```
#!/bin/bash         

echo "Wipe & update Started Please Wait"
./rustserver stop
sleep 30s
rm /home/rust1/serverfiles/oxide/data/Kits_Data.json /home/rust1/serverfiles/oxide/data/PlayerRanks.json /home/rust1/serverfiles/oxide/data/ServerRewards/player_data.json
echo "Plugin Data Deleted Successfully"
Sleep 2s
echo "Full Wipe Starting"
./rustserver wipeall
echo "Full Wipe Process Completed"
sleep 10s
echo "Updating Rust Now"
./rustserver update
sleep 120s
echo "Updating Oxide"
./rustserver mods-update
sleep 120s
Echo "Updates Completed Starting The Server!"
 
```

the other issue is I'm putting time delays in because i dont know how to get my script to interact with the other one
(ie)
./rustserver stop 
this will start a 'softstop' which can take upto 30 seconds, then says something like 'server stopped' but my scripted doesnt know that so i have to just make it wait x seconds?

Thanks in advance for any help

this is the script I'm trying to control from LGSM: [https://pastebin.com/Rpd0sQzi](https://pastebin.com/Rpd0sQzi)

---

### Post by howefield on 2019-11-09
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by SeijiSensei on 2019-11-09
./rustserver will only work if you're in the directory where rustserver is stored. Use a full path like /usr/local/bin/rustserver or whatever.

Also, I'm assuming you've marked your script executable, right?

---

### Post by TheFu on 2019-11-09
The output from 1 command can be read by a shell script.  
OR
the return code/exit status from the prior program can be checked by reading $#.  In Unix, a zero (0) exit means everything is fine.  A non-zero exit means something else happened.

For learning more about bash scripting with lots of examples, google these:
* Beginning Bash Scripting Guide
* Advanced Bash Scripting Guide
* man bash
* Unix Power Tools

---

