---
title: "Vivid: Restart Samba"
date: 2015-04-02
forum: Ubuntu Development Version
---

### Post by gmport on 2015-04-02
I'm trying out Vivid. After installing samba and setting up, I tried to start it with:
```
sudo restart smbd
```
This returned:
```
restart: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
```
Realising Vivid is using Systemd. So I then tried:
```
sudo systemctl restart smb.service
```
And got:
```
Failed to restart smb.service: Unit smb.service failed to load: No such file or directory.
```
Could someone tell me the correct command.

Regards
gmport

---

### Post by zika on 2015-04-02
[FONT=monospace]smbd.service is name of service in SystemD.
[/FONT][FONT=monospace]nmbd.service might also need restart.[/FONT]

---

### Post by gmport on 2015-04-02
Thank you Zika that works and nmbd does need restarting.

Best regards
gmport

---

### Post by Fernando_Jara on 2016-01-17
I have the same issue. 
Could you please provide me the steps to fix it?

Thanks in advance.

---

### Post by Cavsfan on 2016-01-17
> **zika said:**
> [FONT=monospace]smbd.service is name of service in SystemD.
[/FONT][FONT=monospace]nmbd.service might also need restart.[/FONT]

> **Fernando_Jara said:**
> I have the same issue. 
Could you please provide me the steps to fix it?

Thanks in advance.

```
sudo systemctl restart [FONT=monospace]smbd[/FONT].service
```

```
sudo systemctl restart [FONT=monospace]nmbd[/FONT].service
```

---

### Post by Doug S on 2016-02-06
> **Cavsfan said:**
> ```
sudo systemctl restart [FONT=monospace]smbd[/FONT].service
```

```
sudo systemctl restart [FONT=monospace]nmbd[/FONT].service
```Aghhh, thanks. Been looking for hours. I 've just been re-booting, but now I need to be able to restart without booting and "sudo restart smbd" (as suggested in the Ubuntu serverguide) no longer works.

EDIT: I guess we have a pile of work to do for the 16.04 Ubuntu serverguide.

---

### Post by Cavsfan on 2016-02-06
> **Cavsfan said:**
> ```
sudo systemctl restart [FONT=monospace]smbd[/FONT].service
```

```
sudo systemctl restart [FONT=monospace]nmbd[/FONT].service
```

> **Doug S said:**
> Aghhh, thanks. Been looking for hours. I 've just been re-booting, but now I need to be able to restart without booting and "sudo restart smbd" (as suggested in the Ubuntu serverguide) no longer works.

EDIT: I guess we have a pile of work to do for the 16.04 Ubuntu serverguide.

I actually know nothing about it. I just put 2 and 2 together from what Zika was saying. Glad it helped though.

---

