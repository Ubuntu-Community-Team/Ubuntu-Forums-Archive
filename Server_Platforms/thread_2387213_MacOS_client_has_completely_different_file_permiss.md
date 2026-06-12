---
title: "MacOS client has completely different file permissions from Ubuntu Server"
date: 2018-03-16
forum: Server Platforms
---

### Post by mr.robotx on 2018-03-16
So we have a problem at our company... We got a new server and we are using Ubuntu Server 17.10. The Samba Version we have installed is 4.6.7-Ubuntu.
  The problem is that we have these permissions on the server:
  ```
drwxr-xr-x 3 corpuser corpuser 4096 Mar 9 2017 virtuell1/
drwxr-xr-x 4 corpuser corpuser 4096 Oct 12 2011 virtuell10/
drwxr-xr-x 3 corpuser corpuser 4096 Jun 16 2014 virtuell2/
drwxr-xr-x 3 corpuser corpuser 4096 Feb 24 2014 virtuell3/
drwxr-xr-x 3 corpuser corpuser 4096 Jun 24 2016 virtuell4/
drwxr-xr-x 3 corpuser corpuser 4096 Jul 22 2016 virtuell5/
drwxr-xr-x 4 corpuser corpuser 4096 Jan 22 10:25 virtuell6/
drwxr-xr-x 3 corpuser corpuser 4096 May 11 2017 virtuell7/
drwxr-xr-x 5 corpuser corpuser 4096 Jan 16 12:24 virtuell8/
drwxr-xr-x 3 corpuser corpuser 4096 Mar 28 2014 virtuell9/

```  and when we access the server as a client in MacOS (Version: 10.12.6) we get to see these permissions:
  ```
drwx------  1 mr.robot  staff      16384  9 Mär  2017 virtuell1
drwx------  1 mr.robot  staff      16384 12 Okt  2011 virtuell10
drwx------  1 mr.robot  staff      16384 16 Jun  2014 virtuell2
drwx------  1 mr.robot  staff      16384 24 Feb  2014 virtuell3
drwx------  1 mr.robot  staff      16384 24 Jun  2016 virtuell4
drwx------  1 mr.robot  staff      16384 22 Jul  2016 virtuell5
drwx------  1 mr.robot  staff      16384 22 Jan 10:25 virtuell6
drwx------  1 mr.robot  staff      16384 11 Mai  2017 virtuell7
drwx------  1 mr.robot  staff      16384 16 Jan 12:24 virtuell8
drwx------  1 mr.robot  staff      16384 28 Mär  2014 virtuell9

```  This is not what we are expecting to see and we have absolutely zero clue as to why this might be happening... We want the permissions for the client to be the exact same as on the server and we are all signed in as "corpuser" in Samba.
  We did try to solve it using this [solution]("https://superuser.com/questions/1163422/samba-file-permissions-linux-server-mac-client/"), but sadly this didn't help us...

  If you have any Idea then please feel free to comment or answer.

---

### Post by Morbius1 on 2018-03-16
It's not clear to me why you want them to match.

** What you posted looks normal and exactly the same thing would happen if the client was running Ubuntu.

** If the permissions on the client matched the permissions on the server mr.robot would not have write access to the share.

** Unless you added it yourself you probably don't have a corpuser user on the mac anyway.

The username and password you pass to the server to access the share is relative to the server. It does not translate to the ownership or mode of the client. When mr.robot creates a new file on the share it will show up as being owned by mr.robot on the client and corpuser on the server because corpuser is the one who logged into the server.

---

### Post by mr.robotx on 2018-03-16
> **Morbius1 said:**
> It's not clear to me why you want them to match.

I don't think you really get what the problem is about (no offense, maybe I explained it wrong).
We once had a problem where we copied a php file onto a server and it had the wrong permissions. It couldn't be executed.

> **Morbius1 said:**
> ** Unless you added it yourself you probably don't have a corpuser user on the mac anyway.
We added it.

---

### Post by QIII on 2018-03-16
Moved to Server Platforms.

---

### Post by mr.robotx on 2018-03-19
*bump*

---

### Post by mr.robotx on 2018-03-20
*bump :)*

---

### Post by mr.robotx on 2018-03-21
*bump* If you have any questions you can ask :)

---

