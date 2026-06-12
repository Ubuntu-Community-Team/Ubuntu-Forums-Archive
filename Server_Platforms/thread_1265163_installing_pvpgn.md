---
title: "installing pvpgn"
date: 2009-09-13
forum: Server Platforms
---

### Post by I WILL DO IT on 2009-09-13
installing pvpgn
ok, thx 4 all your help


i have a 2wire568: check this box

Allow all applications (DMZplus mode) – Set the selected computer in DMZplus mode. All inbound traffic, except traffic which has been specifically assigned to another computer using the “Allow individual applications” feature, will automatically be directed to this computer. The DMZplus-enabled computer is less secure because all unassigned firewall ports are opened for that computer.

Current DMZplus computer: cool-desktop
Note: Once DMZplus mode is selected and you click DONE, the system will issue a new IP address to the selected computer. The computer must be set to DHCP mode to receive the new IP address from the system, and you must reboot the computer. If you are changing DMZplus mode from one computer to another computer, you must reboot both computers.





And i still can't get team speak-server nore pvpgn

this is the error msg:



(Teamspeak-server)
cool@cool-desktop:~$ teamspeak-server
Exception EFCreateError in module teamspeak-server.real at 0806F095.
Cannot create file "/usr/lib/teamspeak-server/server.ini". Permission denied.
cool@cool-desktop:~$ sudo teamspeak-server
Error, Either an old instance of teamspeak is still running, or
an other application is using the tcpquery port!
Error, Server was not started!
cool@cool-desktop:~$ sudo teamspeak-server
Error, Either an old instance of teamspeak is still running, or
an other application is using the tcpquery port!
Error, Server was not started!
cool@cool-desktop:~$






(pvpgn)
cool@cool-desktop:~/Desktop/pvpgn-1.8.5/src$ bnstat
bnstat: could not connect to server "localhost" port 6112 (psock_connect: Connection refused)
bnstat: fatal error during handshake
cool@cool-desktop:~/Desktop/pvpgn-1.8.5/src$ bnstat
bnstat: could not connect to server "localhost" port 6112 (psock_connect: Connection refused)
bnstat: fatal error during handshake
cool@cool-desktop:~/Desktop/pvpgn-1.8.5/src$


Am going to assume that i need to open the ports ect ect right?

---

