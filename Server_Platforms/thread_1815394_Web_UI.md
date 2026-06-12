---
title: "Web UI"
date: 2011-07-31
forum: Server Platforms
---

### Post by zeev.gil on 2011-07-31
Hi Everyone.

Im thinking of moving from Windows Home Server 2011 to Ubuntu for my home server needs as I wan't more flexibility.

I have had a look at some of the things you can do and appslike Webmin and Bacula seem like features I would use.

But I was wondering if there was a friendly Web UI for server files and possibly remote desktoping into the connected (mostly windows) clients.

Ubuntu server will give me a lot more flexibility but I use these features often.

Cheers

---

### Post by arrrghhh on 2011-07-31
> **zeev.gil said:**
> Hi Everyone.

Im thinking of moving from Windows Home Server 2011 to Ubuntu for my home server needs as I wan't more flexibility.

I have had a look at some of the things you can do and appslike Webmin and Bacula seem like features I would use.

But I was wondering if there was a friendly Web UI for server files and possibly remote desktoping into the connected (mostly windows) clients.

Ubuntu server will give me a lot more flexibility but I use these features often.

Cheers

If you feel you need a Desktop Environment (DE) then by all means install the full verison of Ubuntu Desktop.  Do **not** install Ubuntu Server and then throw Desktop on top of it... IMHO it's a complete waste of time and energy.  If you want a DE, use Ubuntu Desktop.  You can run all the same services as if it was Ubuntu Server.

Ubuntu Server is meant to be lean&mean - no DE, no extra packages, etc.  Updates are easier this way, and administration can be performed completely in the CLI.

Just curious, why would you use the server to remote to other machines?  Seems kind of... unnecessary, but I don't know your environment.

---

### Post by zeev.gil on 2011-07-31
I didn't realise they were so similar. Perhaps then I should use the desktop edition and slowly build up the server features from there. No doubt a DE will make things simpler for me when getting started as I'm not all that experienced with Ubuntu.

My server needs are really not all that high. It will mostly be used to manage backups and a web server/development.

The only reason I wanted to use the server to do the remote desktop was because this is how its done in windows home server.  The web interface made it simple to connect to the client computers for the users of the network.

I could install a VNC server on every client computer but I'm not sure... How would remote desktop sessions normally be managed using a small linux server? Or would you just leave it up to the individual clients to set up and configure it on their own.

Thanks for the feedback.

---

### Post by arrrghhh on 2011-07-31
> **zeev.gil said:**
> I didn't realise they were so similar. Perhaps then I should use the desktop edition and slowly build up the server features from there. No doubt a DE will make things simpler for me when getting started as I'm not all that experienced with Ubuntu.

My server needs are really not all that high. It will mostly be used to manage backups and a web server/development.

The only reason I wanted to use the server to do the remote desktop was because this is how its done in windows home server.  The web interface made it simple to connect to the client computers for the users of the network.

I could install a VNC server on every client computer but I'm not sure... How would remote desktop sessions normally be managed using a small linux server? Or would you just leave it up to the individual clients to set up and configure it on their own.

Thanks for the feedback.

I guess I don't see the need to RDP/VNC into the client machines... what is the purpose?  For me, it's always the client machines connecting to the server for samba (file sharing), apache (web server) etc.  I connect to the server from other client machines using SSH to manage the server, but I'm just failing to grasp why you would ever need to connect to the client machines from the server itself.  I've never used WHS, so perhaps there's some concept I'm not grasping here...  Would love to hear your reasoning.  I'm sure there's something you can setup that would work, you just need to decide if it's worth it to you to go through that.  If you explain why you're doing it, there might be some other way that need can be filled...

---

### Post by zeev.gil on 2011-08-01
In WHS the server is just used to... manage, i suppose the RDP sessions. It has a web interface which makes this very simple.

The reason it is useful on occasions to RDP into the clients weather through the server or not is because firstly the server is small and a some data is stored on the clients. If the users are in a remote location and are after some files they either need to have the foresight to move them to the server while on site or hopefully the server already has a copy of what ever they are after. I suppose if I had a completely centralised system this would be unnecessary.

A second reason I would do this is because one of the clients is used often for image rendering. It would be useful to be able to RDP into that machine and check on the progress of the render or ever remotely start another render job.

These things are reasonably minor but have been quite useful.

---

### Post by volkswagner on 2011-08-01
> **zeev.gil said:**
> In WHS the server is just used to... manage, i suppose the RDP sessions. It has a web interface which makes this very simple.

The reason it is useful on occasions to RDP into the clients weather through the server or not is because firstly the server is small and a some data is stored on the clients. If the users are in a remote location and are after some files they either need to have the foresight to move them to the server while on site or hopefully the server already has a copy of what ever they are after. I suppose if I had a completely centralised system this would be unnecessary.

I'm still not clear what you mean here.  Do you mean user "A" is in the field, but user "B" wants some data that is not on the server but is on user "A" client machine?  By reading your statement it appears you are speaking of the same user.


> **zeev.gil said:**
> 
A second reason I would do this is because one of the clients is used often for image rendering. It would be useful to be able to RDP into that machine and check on the progress of the render or ever remotely start another render job.

These things are reasonably minor but have been quite useful.

Can't you use a client machine to remote into the render machine?

Are all client machines running MS Windows?

If you absolutely want a DE, you can use Terminal Server Client (tsclient) to RDP into Windows clients.  There are other programs such as Remote Desktop (rdesktop).

You can use VNC if the clients are running Linux/Mac.  A better solution (more responsive and reliable + secure) for users running Linux/Mac would be to use ssh and forward X session.

---

