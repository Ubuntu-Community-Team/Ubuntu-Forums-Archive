---
title: "Visual to terminal mode"
date: 2011-09-09
forum: Server Platforms
---

### Post by maxianicu on 2011-09-09
I installed Ubuntu Server 10.04 , after that i installed via terminal "lxde" , to make work easy . And i have one question , how to switch back to terminal mode (without uninstall lxde) ? i don't want to open LXDE ,but pure ubuntu server !

---

### Post by nothingspecial on 2011-09-09
If I recall (it's a long time since I used lxde), I think that the command is ```
sudo service lxdm stop
```

---

### Post by maxianicu on 2011-09-09
> **nothingspecial said:**
> If I recall (it's a long time since I used lxde), I think that the command is ```
sudo service lxdm stop
```

thank you very much ! it works !

---

### Post by cj13579 on 2011-09-09
If you want to be able to switch between the two you should be able to use ctrl+alt+F1 to go to terminal mode and ctrl+alt+f7 to go your GUI.

---

