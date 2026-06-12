---
title: "UFW SSH problem"
date: 2008-11-05
forum: Server Platforms
---

### Post by vorgusa on 2008-11-05
I am not a 100% sure this is an ufw problem, but I have installed Ubuntu 8.10 Server on my home server and put OpenSSH server one it.  I have connected and everything works fine.  I decided to use the firewall on the computer, but since I could not get the profiles to work with the commands I decided to use ports... so the command I used was:

sudo ufw allow from 192.168.1.0/24 to 192.168.1.5 port 22

this should allow all TCP and UDP traffic to the server (192.168.1.5).  It worked right off the bat and I was able to ssh, of course the connection was already made so it should keep working till the server drops the connection.  The next day I tried connecting and it lets me try to log in but after I put the password in it says "connection closed by 192.168.1.5"  nmap says port 22 is open.  I do not understand how this could happend but it really frustrates me!!!!   any ideas?  

I have tried clearing the know-hosts and reconnecting, unfortunately I do not have any other users on the server to test with and this is a headless server that is a pain to get to... I will probably start working on it tomorrow, but I wanted to get some ideas before I take it apart to add a video card.

---

### Post by vorgusa on 2008-11-07
ok.. no response.. I found out that it is not an SSH problem, but a problem with the Server.  I can not login to the box even with a monitor and keyboard.  I type in my username and password and it just shows another Login option.   My password is not incorrect because when I put an incorrect password it tells me.  Anyone know if this can be fixed.. its not like I can get into the box to fix it

---

