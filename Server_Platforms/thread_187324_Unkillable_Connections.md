---
title: "Unkillable Connections"
date: 2006-06-02
forum: Server Platforms
---

### Post by squidward_tentacles on 2006-06-02
OK, Im sure this is a total noob question, but I cannot dissconnect whatever is connected at port 443. Ive tried,
sudo fuser -v 443/tcp <no result> &
sudo fuser -vk 443/tcp <also with no results>
My understanding is that these and <another connection I cant seem to get rid of  running on 9001>, are all associated with tor. My questionable firewall connections are listed as;

192.168.1.100  18.244.0.144  443  HTTPS
192.168.1.100  222.94.11.129 443 HTTPS
192.168.1.100  213.113.27.69 9001 Unknown

none of these connections are listed as tor, in the program colum of firestarter, and despite everything Ive tried I cant get rid of them <plays creppy music>....Ive tried "sudo killall tor", locking the firewall, rebooting and even editing iptables; "sudo iptables -A INPUT -s 213.113.27.69 -j DROP" for each of the connects, and STILL they are there glaring at me with unspoken menance....can anyone confirm this is normal, or if not how to close these connections, and what they might be doing there? It would be a great burden off my mind, Thanks!:neutral:

---

