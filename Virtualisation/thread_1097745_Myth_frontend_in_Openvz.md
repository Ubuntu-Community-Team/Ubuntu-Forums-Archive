---
title: "Myth frontend in Openvz?"
date: 2009-03-16
forum: Virtualisation
---

### Post by smbm on 2009-03-16
Hi

I'm looking to turn my combined (for the time being) myth frontend/backend, samba server into a virtualized server because I want to add some internet facing functionality to it without compromising the security of the other services running on it.

I'm doing it this way to keep hardware/power costs down as the server as it stands is massively overpowered for what it's doing. It seems like a good solution.

My limited research to date (I'm pretty much a newcomer to virtualization)
is that Openvz will be the most suitable for most of my requirements. The only thing I'm not too sure about is the mythtv stuff.

Therefore my questions are: 

Is it possible to run a myth frontend in an openvz container? 

Has anyone any experience of doing this?

Does anyone know if it would have to be in the same one as the backend? 

Would there be any problem with accelerated graphics and what have you? 

Would it be better off running on the host? 

Is any of the above feasible? 

Thanks very much for your help in advance.

---

### Post by jtpiano on 2009-03-16
It is my understanding that you should not try to run a frontend in a VM.  The performance is terrible.  Running the backend server as a VM is just fine.  You'll need a separate frontend.

---

