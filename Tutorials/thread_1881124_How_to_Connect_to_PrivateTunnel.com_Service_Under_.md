---
title: "How to Connect to PrivateTunnel.com Service Under Ubuntu 11.10"
date: 2011-11-14
forum: Tutorials
---

### Post by z3r0-1 on 2011-11-14
[FONT=Liberation Serif, serif][SIZE=3]This tutorial will explain how to connect to the VPN service “PrivateTunnel.com” using Ubuntu 11.10's default network manager (“nm-connection-manager”). [/SIZE][/FONT] 
 

 
[LIST]
[*][FONT=Liberation Serif, serif][SIZE=3]Install “openvpn” and “network-manager-openvpn-gnome”[/SIZE][/FONT]
[LIST]
[*][FONT=Liberation Serif, serif][SIZE=3]Search for them under the Ubuntu Software Center, or...[/SIZE][/FONT]
[*][FONT=Liberation Serif, serif][SIZE=3]Run the following commands in your favourite CLI:[/SIZE][/FONT]
[LIST]
[*]“[FONT=Liberation Serif, serif][SIZE=3]sudo apt-get install openvpn”[/SIZE][/FONT]
“[FONT=Liberation Serif, serif][SIZE=3]sudo apt-get install network-manager-openvpn-gnome”[/SIZE][/FONT]
[/LIST]
  
[/LIST]
 
[*][FONT=Liberation Serif, serif][SIZE=3]Download your PrivateTunnel.com user profile[/SIZE][/FONT]
[LIST]
[*][FONT=Liberation Serif, serif][SIZE=3]Login to [https://www.privatetunnel.com/](https://www.privatetunnel.com/)[/SIZE][/FONT]
[*][FONT=Liberation Serif, serif][SIZE=3]Click on “my account”[/SIZE][/FONT]
[*][FONT=Liberation Serif, serif][SIZE=3]Find         the section that reads “Download User Profile” and click on the         link to download your profile. It will be named “client.ovpn”[/SIZE][/FONT]
[/LIST]
 
[/LIST]
 
 
[LIST]
[*][FONT=Liberation Serif, serif][SIZE=3]Open     client.ovpn with a text editor. Export the “User Certificate”     “CA Certificate” “Private Key” and the “Key File” to     individual text files:[/SIZE][/FONT]
[LIST]
[*][FONT=Liberation Serif, serif][SIZE=3]Look         through your “client.ovpn” file and find the <ca> </ca>         tags. Copy that section into a text file named “CA.pem” (Don't         include the tags).[/SIZE][/FONT]
[*][FONT=Liberation Serif, serif][SIZE=3]Look         through your “client.ovpn” file and find the <cert>         </cert> tags. Copy that section into a text file named         “UC.pem” (Don't include the tags).[/SIZE][/FONT]
[*][FONT=Liberation Serif, serif][SIZE=3]Look         through your “client.ovpn” file and find the <key> </key>         tags. Copy that section into a text file named “PK.pem” (Don't         include the tags).[/SIZE][/FONT]
[*][FONT=Liberation Serif, serif][SIZE=3]Look         through your “client.ovpn” file and find the <tls-auth>         </tls-auth> tags. Copy that section into a text file named         “tls-auth.key” (Don't include the tags).[/SIZE][/FONT]
[*][FONT=Liberation Serif, serif][SIZE=3]Now         move CA.pem, UC.pem, PK.pem, tls-auth.key, and client.ovpn to         /etc/openvpn[/SIZE][/FONT]
[/LIST]
 
[*][FONT=Liberation Serif, serif][SIZE=3]Create     a new VPN connection to PrivateTunnel.com[/SIZE][/FONT]
[LIST]
[*][FONT=Liberation Serif, serif][SIZE=3]Click         on the network icon (in the taskbar)>VPN Connections>Configure         VPN...  or you can open the Network Connections by pressing ALT-F2         and typing “nm-connection-editor”[/SIZE][/FONT]
[*][FONT=Liberation Serif, serif][SIZE=3]Go         to the VPN tab and click “Add”. It's going to ask for your         connection type. Choose “OpenVPN” as your connection type. Name         it PrivateTunnel.com[/SIZE][/FONT]
[/LIST]
     
[*][FONT=Liberation Serif, serif][SIZE=3]Enter     the following configuration settings:[/SIZE][/FONT]
[LIST]
[*][FONT=Liberation Serif, serif][SIZE=3]Gateway:         us.shieldexchange.com[/SIZE][/FONT]
[*][FONT=Liberation Serif, serif][SIZE=3]Type:         “Certificates (TLS)”[/SIZE][/FONT]
[*][FONT=Liberation Serif, serif][SIZE=3]User         Certificate: *use your *“UC.pem” *file*[/SIZE][/FONT]
[*][FONT=Liberation Serif, serif][SIZE=3]CA         Certificate: *use your *“CA.pem”         *file*[/SIZE][/FONT]
[*]         [FONT=Liberation Serif, serif][SIZE=3]Private Key: *use         your *“PK.pem” *file*[/SIZE][/FONT]
[*]         [FONT=Liberation Serif, serif][SIZE=3]Private Key         Password: use the password for PrivateTunnel.com[/SIZE][/FONT]
[*]         [FONT=Liberation Serif, serif][SIZE=3]Click on         Advanced...[/SIZE][/FONT]
[LIST]
[*]             [FONT=Liberation Serif, serif][SIZE=3]Enable the             following options:[/SIZE][/FONT]
[LIST]
[*]                 [FONT=Liberation Serif, serif][SIZE=3]Use custom                 gateway port: 1194[/SIZE][/FONT]
[*]                 [FONT=Liberation Serif, serif][SIZE=3]Use custom                 renegotiation interval 604800[/SIZE][/FONT]
[*]                 [FONT=Liberation Serif, serif][SIZE=3]Use LZO data                 compression[/SIZE][/FONT]
[/LIST]
 
[*]             [FONT=Liberation Serif, serif][SIZE=3]Under the “TLS             Authentication” tab...[/SIZE][/FONT]
[LIST]
[*]                 [FONT=Liberation Serif, serif][SIZE=3]enable “Use                 additional TLS authentication”[/SIZE][/FONT]
[*]                 [FONT=Liberation Serif, serif][SIZE=3]Key file: *use                 your *“tls-auth.key” *file*[/SIZE][/FONT]
[*]                 [FONT=Liberation Serif, serif][SIZE=3]Key direction:                 1[/SIZE][/FONT]
[*]                 [FONT=Liberation Serif, serif][SIZE=3]Click OK[/SIZE][/FONT]
[*]                 [FONT=Liberation Serif, serif][SIZE=3]Un-check                 “Available to all users” (or if you want to have the VPN                 connection available to all users, leave it checked)[/SIZE][/FONT]
[*]                 [FONT=Liberation Serif, serif][SIZE=3]Click Save...[/SIZE][/FONT]
[/LIST]
         
[/LIST]
     
[/LIST]
 
[/LIST]
  

  [FONT=Liberation Serif, serif][SIZE=3]And you're done. You should now be able to connect to the PrivateTunnel.com VPN without touching the command line.[/SIZE][/FONT]
  [FONT=Liberation Serif, serif][SIZE=3]You can connect by clicking on the network icon>VPN Connections>PrivateTunnel.com[/SIZE][/FONT]

---

### Post by xylo04 on 2013-04-11
Thanks! These instructions worked for me in 12.10 Quantal Quetzal, with the following modifications:
[LIST=1]
[*]> Now move CA.pem, UC.pem, PK.pem, tls-auth.key, and client.ovpn to /etc/openvpn
From my limited experience with PKI, I'm guessing that at least some of the .ovpn, .pem and .key files are sensitive. If you're not going to allow other users on the computer to connect with the VPN, it's probably advisable to not put them in /etc/openvpn. I put them in my home directory under ~/.ovpn, and locked down the file system permissions with ```
chmod 700 .ovpn
``` and ```
chmod 400 *.key *.pem *.ovpn
```
[*]> Gateway: us.shieldexchange.com
That gateway URL didn't work for me and gave me an error (something about incorrect VPN secrets), so I used the gateway URL listed in my .ovpn file, which happened to be us-ca-sj-001.privatetunnel.com.
[/LIST]
Otherwise, it's working great! I'm posting over it now. Thanks again, z3r0-1!

---

### Post by lisati on 2013-04-11
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

