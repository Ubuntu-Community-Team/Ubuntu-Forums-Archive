---
title: "Which one is the best Terminal Server for ubuntu?"
date: 2008-04-18
forum: Server Platforms
---

### Post by aloaiza on 2008-04-18
Hello, i want to install a terminal server on my ubuntu but i dont know which one is best at this time? freeNX, LTSP, xrdp, XDMCP, can anyone tell me about the experiences with each one of them, and whos got the better client? 
better client= windows and linux client, fast, easy to use, friendly.
Thanks a lot!.

---

### Post by MrFSL on 2008-04-18
XDMCP is their by default so might as well start with that one. 

Not, exactly sure what you mean about: "Terminal Server."

Are you talking about a Thin Client setup? "Remote Desktop"? Termainal services such as SSH?

What do you want to use it for?

---

### Post by HermanAB on 2008-04-18
Just use SSH.  It is secure and it 'just works' (TM).

---

### Post by solcott on 2008-04-18
I used NoMachineNX on Ubuntu a couple years back (I think it was on 5.04) when I was renting my machine as a game server and it worked very well, but I was a little turned off by only be able to host to one client which was one of the restrictions of the free version.

I was using NoMachineNX because I just couldn't get freeNX working :roll:

---

### Post by aloaiza on 2008-04-18
by terminal server i mean remote desktop administration, i dont mean vnc or ssh administration.

---

### Post by HermanAB on 2008-04-18
Well, that is what SSH does and it is secure too.

$ ssh user@server "gnome-panel"

La voila...

SSH is very advanced, but the simple things are very easy to do - buy the Snail book.

Cheers,

Herman

---

