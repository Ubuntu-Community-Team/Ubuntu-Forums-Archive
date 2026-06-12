---
title: "Starting a virtual Windows on server without X"
date: 2009-07-02
forum: Virtualisation
---

### Post by dentharg on 2009-07-02
Hi!

I am looking for a way to install Windows XP in virtual environment without displaying any graphical interface or hide it at start.

I need to host a small MSSQL database and I wouldn't like to install another machine at home just for that as I already have a Linux server. So the virtual XP would start with the rest of the system as a "service". The only access needed to such XP install would be via RDP.

---

### Post by cybergalvez on 2009-07-02
virtualbox will let you start a VM in headless mode which is exactly what you want

---

### Post by dentharg on 2009-07-02
Thanks a lot! Now this is *exactly* what I needed.

---

### Post by Cheesemill on 2009-07-02
I use VMware Server at work running on a minimal 8.04 Server install.
It works great as all of the VMware config is done through a web app so no need for a GUI on the server.

---

