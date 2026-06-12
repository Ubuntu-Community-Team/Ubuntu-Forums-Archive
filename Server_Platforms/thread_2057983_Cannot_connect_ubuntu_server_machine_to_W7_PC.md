---
title: "Cannot connect ubuntu server machine to W7 PC"
date: 2012-09-14
forum: Server Platforms
---

### Post by Broosta on 2012-09-14
Hi, I'm having trouble connecting my ubuntu server 12.04 machine to my main pc (windows 7).

I built the server a few days ago with new bits. Installed ubuntu server 12.04 and it works ok. 
I want to see the server from my main w7 pc and I can't.
I can connect with windows remote desktop but I can't see any icons on the server, only the blank ubuntu screen without any menus or files or folders that I can access.

Its ethernet connected.

Both server and main pc have internet access.

Please help, this is really doing my head in as I've been at it solidly the last 3 days!

---

### Post by Jeremy Davison on 2012-09-14
Hi Broosta. Just wanted to ask a few questions. Out of curiosity what are trying to do on the server? Are you trying to run bash commands, or are you looking to remotely have a full on GUI you can connect to?

---

### Post by Broosta on 2012-09-14
I'm just trying to use the machine to store movies, photos and music. And then stream from there to my main pc, my squeezebox and my popcorn hour A210 - all over cat5e/6.

I want to download torrents to the server also, not sure if I want the bit torrent client on the server or the main pc though.

Ideally I would like it to run headless with remote access, but I suppose most of the activity will be from my w7 pc accessing files that are network shared without using remote access.

I'm still not 100% sure if ubuntu server is the OS I really need but I'm gonna try it out and see.

---

### Post by Jeremy Davison on 2012-09-14
Hang on. Doing a quick lookup. I may have something.

---

### Post by Broosta on 2012-09-14
Cool, cheers for the advice.
I'll try it out and see if its more user friendly.

---

### Post by Broosta on 2012-09-14
Oh just saw your updated your post. Sounds interesting...

---

### Post by megamister on 2012-09-14
Otherwise another issue with Win7 and Vista accessing a Samba server is fixed with this info I found after hours of researching. Only to find a couple simple little fixes.

Basically, you have to add a DWORD value called LmCompatibilityLevel to:

HKLM|System|CurrentControlSet|Control|Lsa and set the value to 2.
LmCompatibilityLevel


Explanation:

HKLM\SYSTEM\CurrentControlSet\Control\Lsa
Data type
Range
Default value

REG_DWORD
0–5
0


Description

Specifies the mode of authentication and session security to be used for network logons.
Value
Meaning

0
Clients use LM and NTLM authentication, but they never use NTLMv2 session security. Domain controllers accept LM, NTLM, and NTLMv2 authentication.

1
Clients use LM and NTLM authentication, and they use NTLMv2 session security if the server supports it. Domain controllers accept LM, NTLM, and NTLMv2 authentication.

2
Clients use only NTLM authentication, and they use NTLMv2 session security if the server supports it. Domain controller accepts LM, NTLM, and NTLMv2 authentication.

3
Clients use only NTLMv2 authentication, and they use NTLMv2 session security if the server supports it. Domain controllers accept LM, NTLM, and NTLMv2 authentication.

4
Clients use only NTLMv2 authentication, and they use NTLMv2 session security if the server supports it. Domain controller refuses LM authentication responses, but it accepts NTLM and NTLMv2.

5
Clients use only NTLMv2 authentication, and they use NTLMv2 session security if the server supports it. Domain controller refuses LM and NTLM authentication responses, but it accepts NTLMv2.
Activation method

You must restart Windows to make changes to this entry effective.

Note

To set a client running Windows NT Service Pack 4 to level 3 security or higher, the domain controllers for the user's account domains must already be upgraded to Service Pack 4.

For more information about operating-system interoperability and session security settings , see the Microsoft Knowledge Base link on the Web Resources page. Search the Knowledge Base for Article Q147706 or for the keywords LM authentication.






**** For inability to access password share as standard user

to configure the EnableLinkedConnections registry value
Click Start, type regedit in the Start programs and files box, and then press ENTER.
Locate and then right-click the registry subkey

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Curr entVersion\Policies\System.

Point to New, and then click DWORD Value.
Type EnableLinkedConnections, and then press ENTER.
Right-click EnableLinkedConnections, and then click Modify.
In the Value data box, type 1, and then click OK.

---

### Post by Broosta on 2012-09-15
Ok I think this problem can be broken down into two parts.

1 - make ubuntu server able to be controlled from W7 using windows remote desktop.

2 - make the HDDs that are in the server show up in the W7 PC in 'My Computer'.


So just to recap, I have 2 machines - one with windows 7 on and one with ubuntu server 12.04 on.

The server machine has ubuntu desktop installed over the top of ubuntu server, and 4 HDDs.

HDD 1 - ubuntu server 12.04 operating system and nothing else - formatted a few days ago.

HDDs 2-4 - all formatted by ubuntu server 10.04 and have files on - formatted over 1yr ago.

Surely there is just something simple I have to do to make it work?

---

### Post by Broosta on 2012-09-15
> **megamister said:**
> Otherwise another issue with Win7 and Vista accessing a Samba server is fixed with this info I found after hours of researching. Only to find a couple simple little fixes.

Basically, you have to add a DWORD value called LmCompatibilityLevel to:

HKLM|System|CurrentControlSet|Control|Lsa and set the value to 2.
LmCompatibilityLevel


Explanation:

HKLM\SYSTEM\CurrentControlSet\Control\Lsa
Data type
Range
Default value

REG_DWORD
0–5
0


Description

Specifies the mode of authentication and session security to be used for network logons.
Value
Meaning

0
Clients use LM and NTLM authentication, but they never use NTLMv2 session security. Domain controllers accept LM, NTLM, and NTLMv2 authentication.

1
Clients use LM and NTLM authentication, and they use NTLMv2 session security if the server supports it. Domain controllers accept LM, NTLM, and NTLMv2 authentication.

2
Clients use only NTLM authentication, and they use NTLMv2 session security if the server supports it. Domain controller accepts LM, NTLM, and NTLMv2 authentication.

3
Clients use only NTLMv2 authentication, and they use NTLMv2 session security if the server supports it. Domain controllers accept LM, NTLM, and NTLMv2 authentication.

4
Clients use only NTLMv2 authentication, and they use NTLMv2 session security if the server supports it. Domain controller refuses LM authentication responses, but it accepts NTLM and NTLMv2.

5
Clients use only NTLMv2 authentication, and they use NTLMv2 session security if the server supports it. Domain controller refuses LM and NTLM authentication responses, but it accepts NTLMv2.
Activation method

You must restart Windows to make changes to this entry effective.

Note

To set a client running Windows NT Service Pack 4 to level 3 security or higher, the domain controllers for the user's account domains must already be upgraded to Service Pack 4.

For more information about operating-system interoperability and session security settings , see the Microsoft Knowledge Base link on the Web Resources page. Search the Knowledge Base for Article Q147706 or for the keywords LM authentication.






**** For inability to access password share as standard user

to configure the EnableLinkedConnections registry value
Click Start, type regedit in the Start programs and files box, and then press ENTER.
Locate and then right-click the registry subkey

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Curr entVersion\Policies\System.

Point to New, and then click DWORD Value.
Type EnableLinkedConnections, and then press ENTER.
Right-click EnableLinkedConnections, and then click Modify.
In the Value data box, type 1, and then click OK.
Thanks for the advice.
Don't know why but when I last posted your post wasn't there, odd. Also I subscribed to this thread and its not sending me emails like I told it to.

To be honest I have no idea how to change things or even where to find the things that need changing! So I think your idea is beyond me.
But also I had my W7 PC doing exactly what I wanted a few months ago but with ubuntu server 10.04 on the server. The server hardware went wrong so I built another machine and now I'm having problems. Anyway my point is that I just set it up last time and it worked without any changes needing to be made so surely there is some simple thing I need to change in the settings rather than recode stuff?

---

### Post by Elfy on 2012-09-15
*Thread moved to **Server Platforms**.*

---

### Post by Broosta on 2012-09-15
Ok I've solved it!

I needed to put in my full name, not just my first name, when W7 asked when trying to connect the shares in W7 Network places.

Now I need to resolve the remote desktop issue.

I've changed the desktop background in ubuntu on the machine itself, but when I connect to it with remote desktop its the old purpley coloured desktop. Same thing if I open 2 instances of remote desktop - still no menus or icons.

---

