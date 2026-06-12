---
title: "LTSP Guest login"
date: 2008-12-09
forum: Server Platforms
---

### Post by rubbsdecvik on 2008-12-09
Ok, so there has been lots of other posts similar to this, but none that have fully answered my question. 

Let me give a little bit of background. I am not currently in this situation, but it describes my desired outcome well enough so assume the use case is true: I wish to create an Internet/coffee shop with an LTSP server and several PXE booted clients. The system would have several "normal" users, and the server itself would only be accessible by administrators. I've had no trouble configuring a server to have several users. The problem is that I wish to have a destroyable guest session available as well. The idea would be to have "premium" users have their own account and permanent storage space on the server, while non-paying users would get a guest account that would be destroyed.

I would ideally love to have the same sort of environment that the 8.10 guest session option is like, but understand if I can't get something exactly like that.

I've even found this webpage that tells me how I can add a "Log in as Guest" button (which I've gotten to show up, but it doesn't do anything): [https://help.ubuntu.com/community/UbuntuLTSP/AutoLoginFeatures](https://help.ubuntu.com/community/UbuntuLTSP/AutoLoginFeatures)

I ideally would like the button to create a temporary guest session and destroy it when the user logs out.  The reason I would like the session to be created on the fly is that if one user is logged in as guest, other "guest" users can not use firefox etc.

Does anyone know of anyway I can create this type of functionality? Is some sort of kiosk system better?

---

### Post by rubbsdecvik on 2008-12-10
bumb

---

### Post by rubbsdecvik on 2009-03-09
bump

---

