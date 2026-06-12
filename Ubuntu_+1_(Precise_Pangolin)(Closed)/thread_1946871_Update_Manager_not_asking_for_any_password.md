---
title: "Update Manager not asking for any password"
date: 2012-03-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Nick Payne on 2012-03-25
I just booted up 12.04 and started update manager. It found 61 updates which were downloaded and installed, but at no stage did it ask me for a password in order to apply the updates. Never had this happen before, that it could update the system without needing a password. The version of update manager is 1:0.156.9.

---

### Post by agillator on 2012-03-25
I don't remember the specifics but the Update Manager has apparently been changed so it checks for itself to see if you are authorized to update the system. I'm not sure what it does if you are not, probably gives you a rasberry and hides the letter 'i' on your key board or something equally nefarious. Just another step in the computers' plot to take over the world.

---

### Post by philinux on 2012-03-25
> **Nick Payne said:**
> I just booted up 12.04 and started update manager. It found 61 updates which were downloaded and installed, but at no stage did it ask me for a password in order to apply the updates. Never had this happen before, that it could update the system without needing a password. The version of update manager is 1:0.156.9.

Same since a long time ago. It will only ask for a password if New packages are being installed like a new kernel etc.

---

### Post by jasonsmith01 on 2012-03-25
> **Nick Payne said:**
> I just booted up 12.04 and started update manager. It found 61 updates which were downloaded and installed, but at no stage did it ask me for a password in order to apply the updates. Never had this happen before, that it could update the system without needing a password. The version of update manager is 1:0.156.9.

Had it been a while since you updated because I've had no updates available since yesterday morning, about 24+ hrs ago?

---

### Post by Rhaedas on 2012-03-25
Is this behavior just for Update Manager? I'd hope that a password is continued to be asked for regardless of who is logged on, for several reasons of security. Not even sure if I like Update Manager having that kind of control. Is it/will it be configurable?

Added: and I'm assuming this is new for 12.04, since I seem to have to still authorize security updates with my 11.10.

---

### Post by kklimonda on 2012-03-25
> **Rhaedas said:**
> Is this behavior just for Update Manager? I'd hope that a password is continued to be asked for regardless of who is logged on, for several reasons of security. Not even sure if I like Update Manager having that kind of control. Is it/will it be configurable?

Added: and I'm assuming this is new for 12.04, since I seem to have to still authorize security updates with my 11.10.

There is one other change I think - local, active sessions can modify system-wide NetworkManager connections. It's all configurable though by changing the local polkit policy.

---

### Post by philinux on 2012-03-26
> **Rhaedas said:**
> Is this behavior just for Update Manager? I'd hope that a password is continued to be asked for regardless of who is logged on, for several reasons of security. Not even sure if I like Update Manager having that kind of control. Is it/will it be configurable?

Added: and I'm assuming this is new for 12.04, since I seem to have to still authorize security updates with my 11.10.

11.10 update manager will not ask for a password if it's updating software already installed. But a new kernel will need a password.

Thread closed as this has been a feature for some considerable time.

---

### Post by mörgæs on 2012-03-26
Taking the liberty of adding a brief comment. Feel free to re-close.

The reason for this is that entering a password should give the user a sense of 'this might be dangerous'. Entering a password is just as much a message to the user as it is a message to the operative system.

If the password is required for everyday tasks like updating existing packages it will lose its alerting power.

---

