---
title: "Specific .sol Flash cookie, access to and manipulation"
date: 2013-12-17
forum: Ubuntu, Linux and OS Chat
---

### Post by pcar916 on 2013-12-17
Hi Folks,
I hope this is the right place.

Part One:
 I'm trying to copy (repeatedly) my Machinarium.sol file back and forth between my 12.04LTS desktop and and Win7 laptop computers, both of which have the Machinarium game installed.  I'd like to constantly keep that file synchronized so I can be at the  same level in the game regardless of which machine I'm on. 

Part Two: 
 Once that's  worked out, I'll try to figure out how to automate the synchronization  with a script... or FTP, or something else. This is a good little project to get to know more about the Linux file system, so I haven't explored any applications to do this.

What I've tried:

1. I've located the file and copied it from the Win7 box.

2. I've read in several forums that the Linux .sol file is located in the path below, but since I can't yet see below the #SharedObjects directory, I don't know the actual path yet.

/home/-username-/.macromedia/Flash_Player/#SharedObjects/-randomword-/-localthing-/Machinarium/Machinarium.sol

3. In terminal sessions, recursive"ls -al" searches have failed to find the file.  

4. I've tried both as my admin user, and then as root, to get below the .../username/...#SharedObjects directory and failed each time. I don't play the game as root.

5. When I cd into #SharedObjects I get bounced immediately into my home directory

6. I've tried to use chmod (with sudo) to change the permissions of the #SharedObjects directory with no success, but it's likely operator-error in my syntax since it reports a parameter missing that I'm unable to discover so far. Embarrassing newbee situation but true.

Any ideas are appreciated

~Ron

---

