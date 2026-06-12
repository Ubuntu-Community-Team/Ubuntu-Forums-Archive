---
title: "Simple VPN solution with ssh using sshuttle"
date: 2011-05-09
forum: Server Platforms
---

### Post by homerhomer on 2011-05-09
I just got back from LinuxfestNW and I learned about a nifty little program called sshuttle. Sshuttle is a little VPN connection using ssh. If can connect to a remote ssh server then this should work for you.

Attached is a simple little script I wrote to connect. Sorry no network-manager plug-in

*** Just a warning, this program might set off intrusion detection on the remote server, use at your own risk. **

---

### Post by Oxwivi on 2011-05-30
This little thing is simply awesome! I was introduced to it on this [Ask Ubuntu answer]("http://askubuntu.com/questions/45075/how-do-i-route-my-internet-through-a-ssh-tunnel/45110#45110") (note, originally it was a just a copy of the README at project website - I polished it into a small walk-through) when looking for a way to set up a VPN server without admin privileges. It's way better than any 'real' VPN!

By the way, no need need to pull it from Git, it's in the repo for Natty:
```
sudo apt-get install sshuttle
```And can you elaborate a little about that intrusion detection thing?

---

### Post by brettg on 2011-05-31
Alternately, you could try this [5 minute VPN setup guide]("http://tuxnetworks.blogspot.com/2011/05/howto-easiest-vpn-setup-ever.html").

---

