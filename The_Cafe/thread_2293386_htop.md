---
title: "htop"
date: 2015-09-04
forum: The Cafe
---

### Post by brian-mccumber on 2015-09-04
I actually found this thing by accident. I was trying to type in vtop to view processes but I typed in htop instead. Don't ask me how I managed that I don't know, but the terminal informed me that it was available for install. I did a quick search and found it was an even better process viewer/controller that top and vtop so I installed it. I like it. Vtop was also found by accident before I found htop, because my typing is atrocious, but it seemed to me that htop was more of what I wanted in a process viewer. I think it is easier to be able to select the process in question with the arrow keys then hit an f-key to perform an action on the process than to type in strings of characters for the pid and the action you want to perform on it. I like to write programs and sometimes they get stuck and the only way I can end them is to use terminal to stop them and this has saved me some time and aggravation. Anyway I was just throwing this out here, if someone finds it usefull then yay \0/. I think I am going to just start typing random stuff into the terminal to find more things.

You can install htop through the terminal 

```
sudo apt-get install htop
```

and here is it's website - [http://hisham.hm/htop/](http://hisham.hm/htop/) - in case you like to read up on things before installing them.

---

### Post by CharlesA on 2015-09-05
Huh. I've never heard of vtop, but I've used top before I discovered htop.

I like htop.. it's got pretty colours. :p

---

### Post by brian-mccumber on 2015-09-05
I agree it does have pretty colors. After I first installed it, I actually had a game, Terraria, lock up because I left it paused for like 5 hours, apparently the computer did not like that. Anyway so I have the terminal open and I am trying to get htop to kill the pid and it's not working then I remembered, oh I have to sudo it when I run it, so I did and it worked. I am a newb when it comes to Linux, and I forget things sometimes cause I'm old. I just like the fact that I can use the arrow keys to highlight the offending pid and hit a function key to act on it and the fact that it works after you start it the correct way. I have been thinking about maybe putting something like htop in a gui with buttons to push to kill things and blinking lights and bells and whistles and stuff. Ok maybe not the blinking lights and stuff, but a list of processes and a button to press to kill a process that needs killing would be cool. I mean I like messing around in the terminal and whatnot but programs with nice UI's are good too.

And also vtop can be installed via the terminal too, but it is called util-vserver but if you type vtop into the terminal it says vtop is not installed you can install it by typing sudo apt-get install util-vserver.

---

### Post by brian-mccumber on 2015-09-05
Well I went and did a search for graphical process explorer for Ubuntu and apparently someone has beaten me to the punch so I guess someone else thought it'd be a good idea to put something like htop in a GUI too. 

There is one called QPS and then Linux Process Explorer, not really sure how well they work tho, I might have to install them and give them a test drive.

And also Charles, that link in your sig to the security guide was a good read.

---

### Post by CharlesA on 2015-09-05
> **brian-mccumber said:**
> 
And also Charles, that link in your sig to the security guide was a good read.

Thanks! It was a nice collaboration.

I don't think I've ever used htop to kill processes off - I usually just use ps and a grep to find the pid then kill it with the kill command.

---

### Post by brian-mccumber on 2015-09-05
Well as much as I hate to admit it I have used process explorers to kill many processes many times but that's just because I like to write programs like plotting sine waves, spirographs, and fractals and sometimes I don't get them right the first time, go figure,  and I like to have a quick way to kill it off so I can fix what's wrong with it.

---

### Post by brian-mccumber on 2015-09-06
Well after all that and searching for a gui version of htop, I found one that is already installed with Ubuntu, System Monitor. I was using the dash to search for process monitors and it popped up and it is really good. It has Processes tab where you can select and stop errant processes, a Resources tab where it shows cpu, Memory and Swap, and Network history in graphs. It also has a File System tab where it shows the percent of space used and space left on the drives. If you want to check it out open your dash and search for System Monitor. It usually pops up after I only type sys.

---

### Post by flaymond on 2015-09-10
Want to find softwares from terminal? 

Type -

```
apt-cache search randomWords
```

Found a lot of new things with it.

---

