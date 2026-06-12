---
title: "HOWTO: automatic patching of OpenVPN client Certs"
date: 2008-05-16
forum: Security
---

### Post by SpaceTeddy on 2008-05-16
This Document describes (possibly the worst) way of automating the process of revoking vulernable OpenVPN keys and distributing replacement ones. 

Before you start reading thing, let me poing out that:
- i am painfully aware that a broken certificate should NOT be used to issue a new one !
- this solution sucks big time when it comes to reliability ( i can think of about a hundred things that could go wrong with this)
- That the scripts provided will ONLY, and ONLY work with windows clients under a a lot of assumptions.

So, if anyone see's a better way of dealing with this, please **don't hesitate** to tell me. If need be, i will patch the scripts and also test them.
Also, i have NOT tested these scripts in a life enviroment yet. They are only tested with a testbed of three windows clients and one debian server (yes, Debian)

Ok - now that the disclaimers and concerns are said, here is what i accomplished to get working.

Upon connection of a client to the server, the server will run a script which does the following things:
[LIST=6]
[*]check if the client certificate is "bad"
[*] if the certificate is bad, try to connect to the remote computer **via the vpn** (this way i don't have to worry about firewalls, nat, etc)
[*]if the connection succeeds try to mount the C$ share of the client into the server
[*]if the mount succeeds, check if the key and crt file can be found on the client
[*]if the files are found, revoke the client certificate, copy the "old" keys to a different place to keep them (why i don't know, i just want to keep them for now) and generate a new certificate for the client with the same filename and the same commonname
[*] copy the files back to the client.
[/LIST]

When the client connects the next time, it will use the new certificate. Also, the old one will be revoked by then.

Packages you need for doing this:
[LIST]
[*]smbclient
[*]smbfs
[*]openssl
[*]sudo
[*]perl
[/LIST]

Setup:
[LIST]
[*]copy the three supplied scripts into the folder /etc/openvpn/script (any other folder can be chosen - but then the scripts will need to be changed aswell)
[*]edit the scripts variables to match your enviroment. **make sure that ALL variables are set properly**
[*]allow your openvpn user (for me it's nobody) to execute the checkclient.pl as root (i know, security risk - But it's the only way i could figure out how to do it. suggestions welcome for improvements)
[*] make sure your crl.pem is set right (this was a major problem for me)
[*] create a folder "revoked" in your keys dir (this is where the script will move the revoked certificates)
[*] add the line ```
commonName_default = $ENV::KEY_COMMONNAME
``` to your easy-rsa's openssl.cnf for enabling batch mode of certificate generation.
[*] add the client-connect directive to your openvpn configuration and point it to the hook.pl
[*] make sure your clients all run windows and have the C$ share enabled for login. If that is not the case, you will need to modify the fixclient.pl to mount the remote drive some other way.
[*]**TEST YOUR SETUP WITH A DUMMY VPN BEFORE YOU APPLY IT**
[/LIST]

That is pretty much it.

I have left specific instructions on what commands to run out on purpose. If you cannot follow the above steps - ask for help, figure out what exactly the scripts do or change the keys manually. This is a very risky buisness and too many things are unknown to provide specific intructions...

again, any suggestions, help, pointers are welcome. Also, if you have questions, don't hesitate to ask :) I know the scripts are far from perfect.

---

