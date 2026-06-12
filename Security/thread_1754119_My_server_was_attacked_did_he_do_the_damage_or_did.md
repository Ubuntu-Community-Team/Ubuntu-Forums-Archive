---
title: "My server was attacked did he do the damage or did I?"
date: 2011-05-09
forum: Security
---

### Post by TaylorHxx on 2011-05-09
Could someone shed some light on what happened and how i can go about fixing this and preventing it in the future.

Ok  I have had a Ubuntu 10.04 server running on my home network.  I used it  mainly as a file share and a media center server.  I also used it to  host webpages that i used for classes and for learning. It had the full  LAMP install and full support for all the standard web protocols  including email.  In order for the machine to be visible to the Internet  I ran the server in a DMZ off of my router, yes way insecure as I have  learned as it exposed all ports to the internet. 

A couple weeks  ago I installed transmission on it and set it up to be run with the  webui, unfortunatly I never got around to setting the firewall and it  was exposed to the Internet w/o any protection.

  Anyway the  other night I came home drunk and tried to access the webui of  transmission and was told access denied by apache i checked all my conf  files that i know of and permission should have been there. I changed  something(sorry don't remember what believe it may have been .htaccess)  and was able to get to the transmission-daemon however transmission then  told me that my IP address was not allowed. At the same time access was  being denied by apache to all of my web resources.(except webmin)  Though any one that can help me can probally guess it was returning  error 403 for all requests from all ips including request sent via  hidemyass.coms free http proxy.

  I checked my apache access logs  and remember noting some unusual activity but cant remember what( the  logs got cleared since i checked them and lost access and then regained  access to them and are missing everything before may 8 @ ~ 1:30 am). In  the apache error log there were several attempts to access files such as  /var/www/php/, /var/www/myphp/, /phpadmin/, /phpa/ /admin/, and the  list goes on but is shorter than what i would expect for a dedicated  attack leading me to think they may have found an exploit in /wp/ my  wordpress directory. I installed wordpress to see what someone was  talking about but refused to learn it since I can write better webpages  with edit in windows.

  In addition to the things in my apache  log someone has used the hell out of my squid server w/o my knowledge.  I  had squid set up but never truly configured or used it.

Now in  addition to the other two I checked Auth.log to make sure no one had  gained access to my machine.  Starting on march 24 I began recieving  brute force attacks the attacks came from 6 or so different IP's but  only from one IP at any given time, the attacks also seemed to use  different approaches, and at first were seperated by many hours.  Starting may 2 there has been a constant brute force trying to gain  access to the root account. this brute force is from the same ip that  has been using my squid.

 Seeing the bruteforce attempts i  removed my machine from the DMZ and brought it back inside my routers  firewall and changed my routers firewall to strict( denys all packets  inbound and out except for http/imap/pop/....).  Doing this stopped the  brute force i believe since there are no entries of the sort in auth.log  after doing so.

 After taking the server off of the dmz i was  still being denied access to apache. (DLNA and samba were still  working.  Since i thought i had stopped the attack i left the machine up  and went to sleep planning on sorting everything out in the morning  when i was sober.

  When i awoke the next morning my ssh into my  server was still active. I ran ps -ejH and ps aux and saw a process sshd  root@notty. I killed this process thinking it was an active connection  to the person that had been attacking my machine (yes i now know that  notty is not the name of a hackers box but stands for no TTY still what  could have opened the process?).  I then changed my root password from  the fourteen character password to a 29 character password (not sure i  have my computer set to accept one that big it my not have taken more  than the first so many characters that is the default max). I changed  the root password from an ssh shell that i had established from the box  in my room the night before. I also disabled all user accounts other  than my own from webmin. 

another note when i awoke access to  apache was working and all my pages were accessible except for  transmission which still reported a permission denied by ip message, and  samba was having faults sometimes returning a permission denied  sometimes not.
 
After i changed the password i tried netstat from  root and was told permision denied(file permission of the netstat  binary i believe). After this the computer in my room faulted( I keep  having problems with it, even with a fresh install of 10.04.2 LTS, could  use help with that also but thats for another thread), anyways my  computer restarted and my ssh shell was disconnected.

Upon  rebooting and trying to ssh back into my server all ssh access by me had  been blocked. I could not even ssh into my personal account on the  machine protected with a password i use daily.  Though the password was  right, ssh seemed to want a public key. i then tried webmin and though i  could log in webmin showed that none of my servers were installed even  though they are.

Not knowing what to do next I unpluged the  machine from the lan brought it to my room and hooked it up to a good  ol' keyboard and monitor.  I fired it up and it booted into the linux os  and then returned something along the lines of fatal error /sbin/init  not available..... /sbin/init permission denied.
 
well thats the  end of that hard drive residing in that machine.  I pulled the hardrive,  Installed it in my desktop, mounted it and have rw access to it.  My  files system permissions had all been changed from what they were to rw  by user and group but no x on any files that needed it.  I used chmod  0777 on the entire filesystem and can now boot from that harddisk,  however i cannot login to the root account. I also cannot su into any  other accounts besides root. I would try sudo su but i removed su from  the sudeors command list and I cant even run sudo. Sudo should be  allowed by all users in group admin which my account should be part of.  The password for root that i am entering is correct. To ensure that i  have the password right i even copy and pasted the hashed version of the  password to my personal account into the password of the root account  (/etc/shadow file).  Using su i can authenticate the password but i  receive error in setting suid causing su to fail.

Any Ideas what  happened, how the permissions on my file system were changed? If it was  done by an attack, how did they gain access? What is preventing me from  gaining access to root?  What do I do next? I am considering backing up  important data files and reinstalling so i don't have to individually  chmod my whole system back to the proper permissions. When i get it set  back up should i continue to run it dmz off my router but configure ip  tables to allow only the people on my local network access to resources  such as transmission, dlna, samba or should i run it inside my routers  firewall and forward the proper ports through my routers firewall?  What  about ssh even though i dont use it outside of my network how could i  configure it to where i could ssh into my server from over the internet  without exposing it; could i use vpn to establish a connection to my  network and then filter ssh to the internal network that way you would  have to crack my vpn before you could attack my server?  What about vpn  verneralbilities?  What about using Network address translations to make  the machine accessable internet side, i have used it before but had  trouble with updates?  And finally where should i start in securing the  machine for my next install?

I am interested in any comments,  notes recomendations or discussions on network and file system  permissions and security. Hopefully this thread will grow to be a great  security resource for users interested setting up a home server.

 On  I final note I am setting up this server with web access as a learning  tool I am currently in college majoring in computer sciences and hope to  one day be employed as a system analyst designing and implementing  computer networks for corporations.

---

### Post by CandidMan on 2011-05-09
> To ensure that i  have the password right i even copy and pasted the  hashed version of the  password to my personal account into the password  of the root account  (/etc/shadow file
I'm sure that's not kosher, editing the shadow file like that also, you'd need to know the 'salt' before hashing your password.

As for the ssh, are ssh keys a viable option?

---

### Post by bodhi.zazen on 2011-05-09
That is one wall of text.

The short answer is it seems either you were compromised (highly likely) or yoru install has been damaged to the point where I think you need to back up your data and reinstall.

As you can see, a DMZ is not really a good idea, keep it firewalled behind your router.

Forward ports from your router and turn UPnP off.

I personally firewall all private servers (samba, nfs, squid, etc).

Secure ssh with keys.

And you should be good to go.

If you want the longer answer, look at the forensics links in the security sticky. You have already messed with the HD and forensics are thus compromised. Forensics are very time consuming, but you could try.

---

### Post by TaylorHxx on 2011-05-09
Sorry about the wall of text i was trying to keep it short but there was alot of information and i wanted anyone replying to have the same knowledge about it as i do.

I'm about to google uPnP but i have no idea what that is though i have seen it in my routers firewall could you clarify on that.

Second removing the server from DMZ and placing it behind the firewall of my router should have prevented any further access to it.  How would an attacker still be able to access it? Could a "backdoor" have been installed where the server would send an outgoing connection and thus opened a port?

Additionally I have just nmaped my router and port 4367 is open on it when all ports except for my web management ports should be closed i googled port 4367 and found that it is used by a windows virus w32.spyware could you point me in the right direction as to closing this port and resecuring my network

---

### Post by TaylorHxx on 2011-05-09
nevermind about the port i misread it, it is a port kept open by my isp to allow them access

---

### Post by holiday on 2011-05-09
I second bodhi.zazen: carefully pull off your data, wipe the drive, and re-install. 

Install DenyHosts. It will thwart brute force attacks unless they guess lucky in three tries.

And don't drive drunk. If you're planning on working enterprise systems, you really don't want to be the one crashing the bus. You could find yourself in jail.

---

### Post by bodhi.zazen on 2011-05-09
UPnP: [http://en.wikipedia.org/wiki/Universal_Plug_and_Play](http://en.wikipedia.org/wiki/Universal_Plug_and_Play)

Yes there could be any number of backdoors / rootkits.

---

### Post by holiday on 2011-05-09
Oh yeah. You could try chkrootkit.

---

### Post by TaylorHxx on 2011-05-09
SSH keys may be a viable option but I am not familiar with them.  A goal of my server is to have the resources and files that I use at home available from any computer with Internet access, with the proper credentials of course.

---

### Post by TaylorHxx on 2011-05-09
[LEFT]As far as DenyHosts go I remember reading somewhere that you could configure the SSH daemon to limit login tries I plan on implementing that and configuring a firewall such as ufw to limit connection attempts to my ssh port. I think that should be enough along with a secure password to thwart any further brute force attempts like the one I saw. I will look at denyHost also though
[/LEFT]

---

### Post by TaylorHxx on 2011-05-09
> **bodhi.zazen said:**
> 

Forward ports from your router and turn UPnP off.

.

You say you would disable UPnP.   After reading the wiki page you provided I am assuming that this is because a UPnP device could create a port map and thus open a port that could be used in an attack.  However, I have many media players such as blue-ray players that have internet features such as netflix, napster and vudo.  Could disabling UPnP on my router cause problems with any of these devices such as them not being able to connect when i plug them into my network. I have also noticed that some programs Skype and bit torrent clients  more specifically have created entries into my routers firewall at times. Would it prevent skype from creating its entry in my routers firewall? If so this is would not be a viable option for me.

---

### Post by jerome1232 on 2011-05-09
For torrent clients and skype. Yes you would need to manually forward ports. This is the reason I use host based firewalls on any machine that is running services that listen for connections from the outside world.

---

### Post by TaylorHxx on 2011-05-09
Well i think all firewalls are host based being they can allow or deny access to a port based on the address the request is recieved from but yes I will definitley be setting very strict firewalls for private services from now on, unfortunately i do not believe this would have helped this attack after reviewing log files i believe the system was comprimised through an apache exploit, don't ask me which on or how, but i Believe this because at 8 o'clock the night of the attack webilizer generated a report based on apache log files with 20% of my traffic belonging to a browser named ZmEu, which apperently is a verneralbility scanner.  In addition to this my apache logs were cleared probaly to cover the entrance. In which case a host based firewall would do nothing since i would have allowed the access through it.

---

