---
title: "Multi Platform Client server architecture"
date: 2008-12-12
forum: Server Platforms
---

### Post by brijith on 2008-12-12
Hai All,

Is it possible to have an cilent server architecture in which a Windows 2003 server act as server and Ubuntu systems act as clients. So that ubuntu clients can run windows applications installed in the Windows 2003 server.



**[COLOR="Red"]Thanks[/COLOR]**

---

### Post by netztier on 2008-12-12
> **brijith said:**
> Hai All,
Is it possible to have an cilent server architecture in which a Windows 2003 server act as server and Ubuntu systems act as clients. So that ubuntu clients can run windows applications installed in the Windows 2003 server.


As long as there is a proper client software for Ubuntu, there is no objection to running the server software on Windows and the client software on Ubuntu.

Examples might be

Server: IIS Webserver on Windows Server
Client: Firefox Web Browser on Ubuntu client
Protocol: HTTP, HTTPS

or 

Server: some IMAP or POP Mailbox server on Windows Server
Client: Thunderbird or Evolution E-Mail client software on Ubuntu client
Protocol: IMAP, POP3

or

Server: Windows file sharing on Windows Server
Client: SAMBA smb-client software on Ubuntu
Protocol: NetBIOS-over-IP or CIFS


or a bit generalized
[LIST]
[*]a server side software (here: for Windows) that implements a custom or standarized protocol to be accessible over the network.
[*]a client side software (here: for Ubuntu) that implements the User interface and the same protocol, to talk to the sever over the network
[/LIST]

This would be "multiplatform client/server" computing. 


If however you were talking about installing the windows based client side software on a windows server and running it there (while redirecting it's output display to an Ubuntu computer), we'd be talking *remote desktop* or *terminal services*, and we'd be barking up a completely different tree.

Ubuntu comes with a terminal services client installed, so you can access windows based terminal services or remote desktop sessions with the RDP protocol.

Traditionally, the term *client/server* implies having "fat" client software on the desktop and the data repository on the server. 

*Server based computing* is what you hear if you are running terminal services (usually Windows or Citrix), install the the "fat" client software on the server and have the display done with very lightweight RDP or ICA client software, somewhere across the network. Occasionally, these clients aren't even PCs, but special small-scale hardware called *Thin Clients*; they run nothing more than a stripped-down operating system and the RDP/ICA client software.

A nitpicker might argue that this was again *client/server computing*, because you still have a *server* (Windows or Citrix Terminal Services), a *client* (Remote Desktop Client), a common *protocol* (RDP or ICA) being talked across a *network*...  all confusing buzzwords :-)


regards

Marc

---

