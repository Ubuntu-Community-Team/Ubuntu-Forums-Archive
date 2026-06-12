---
title: "ubuntu is blocking ports"
date: 2009-12-29
forum: Security
---

### Post by onesojourner on 2009-12-29
I have never touched my ip tables but something is still blocking port 6676 on me computer. See the screen shot.

---

### Post by FuturePilot on 2009-12-29
Are you behind a router? If you are you probably need to enable UPnP in the router or manually forward the port in the router.

---

### Post by onesojourner on 2009-12-29
yes I am behind a router. I posted the screen shot, the router is set up correctly. this is a problem with ubuntu.

---

### Post by FuturePilot on 2009-12-29
Try adding a torrent then check the port again. IIRC Transmission won't actually forward anything unless there is a torrent active.

---

### Post by onesojourner on 2009-12-29
I started an ubuntu torrent. The port is still closed and I can't upload any data.

---

### Post by sting3r on 2009-12-29
I bet you already checked but is the ufw blocking it?

---

### Post by rookcifer on 2009-12-29
Click on the uPnP box and see what happens.

---

### Post by onesojourner on 2009-12-29
no change. it still says the port is closed.

---

### Post by cariboo on 2009-12-29
I would suggest you use [canyouseeme]("http://canyouseeme.org") to make sure that the port you forwarded on your router is open. you can also check to see if transmission is listening using netstat:

```
netstat -tnlp
```

when you have the program running.

---

### Post by onesojourner on 2009-12-30
I am not sure what happened but it is all working good now. I guess it needed some time to think things over or something.... thanks for all the help.

---

