---
title: "Windows does not ask for new credentials but silently fails when connecting to samba"
date: 2015-04-02
forum: Server Platforms
---

### Post by Antoniya001 on 2015-04-02
I have a samba server in stand-alone mode. Users are students and bring their own windows machines. Now the default computer name and login of course do not map to a proper Linux username or computer name. (LDAP/shadow).

However when they connect to a share, they do not get a prompt for credentials after a failed attempt, but it just gives a reply : "Cannot connect to blabla.."

When using net use [\\server\share]("file://\\server\share") /USER:studentlogin Password  everything of course works as expected, but I do not wish to have to use command prompt to connect.

Is there any way to force a prompt asking for credentials from the server side ?

Arjan

---

### Post by nerdtron on 2015-04-02
You probably already connected to the samba share "before" and you choose it to remember the old password.

maybe the old samba share is still active on windows, Just check: [http://www.howtogeek.com/howto/16196/how-to-disconnect-non-mapped-unc-path-drives-in-windows/](http://www.howtogeek.com/howto/16196/how-to-disconnect-non-mapped-unc-path-drives-in-windows/)

---

### Post by Antoniya001 on 2015-04-02
No that is not it. It is more like it connects as guest to the servers share list ([\\server\IPC$]("file://\\server\IPC$") ?? cannot remember those default shares from memory) and forgets to ask for proper creds when browsing into a share.

But it needs to be server side. I do not wish to "help" students individually, even if incorrect login data is present in net use or credential manager, I should be able to trigger the network login window from server side if incorrect credentials are given.

Any samba options that could trigger that ?

Arjan

---

### Post by bab1 on 2015-04-02
> **Antoniya001 said:**
> No that is not it. It is more like it connects as guest to the servers share list ([\\server\IPC$]("file://\\server\IPC$") ?? cannot remember those default shares from memory) and forgets to ask for proper creds when browsing into a share.

But it needs to be server side. I do not wish to "help" students individually, even if incorrect login data is present in net use or credential manager, I should be able to trigger the network login window from server side if incorrect credentials are given.

Any samba options that could trigger that ?

Arjan
Windows machines advertise the logged in user to the Samba server.  If the user is not known (passwd) and guest access is configured with the following ```
map to guest = Bad User
```
Then that user is [COLOR="#0000FF"]**authenticated**[/COLOR] as the guest defined in the smb.conf file.  The smb.conf default is [CODEguest account = nobody[/CODE]... no guest user is asked for a login.

It is entirely possible that the user is [COLOR="#0000FF"]**authenticated**[/COLOR] as a guest (i.e. the user nobody).  If the user nobody has no [COLOR="#FF0000"]authorization[/COLOR] (Linux permissions)) then that user will not be able to use the data in the shared folder even it the user is [COLOR="#0000FF"]**authenticated**[/COLOR].

[LIST]
[*][COLOR="#0000FF"]**Authenticated**[/COLOR] = who are you
[*][COLOR="#FF0000"]**Authorized**[/COLOR] = you have permission to do that
[/LIST]

How have you configured the [shares]?  Are you using a guest user?  Are your user authenticated but not authorized.

---

