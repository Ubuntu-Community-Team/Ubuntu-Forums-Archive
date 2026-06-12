---
title: "VirtualBox dkms"
date: 2024-09-06
forum: Virtualisation
---

### Post by rachelesther on 2024-09-06
:-k

Hello!

I do not know what I could do now.

Does anyone know what to do?

-Rachel

---

### Post by TheFu on 2024-09-06
[https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html) can help.  The error clearly says there are dependency issues. Fix those.

---

### Post by ajgreeny on 2024-09-06
I never installed **virtualbox-dkms** in a guest Linux OS in the past when I used virtualbox; it is not needed as far as I'm aware but **dkms** will probably be needed in the host Linux OS in order to build some of the utilities in the guest additions that are needed for the guest to run properly. I install **dkms** in all my Linux OSs

You have not given us enough information for anyone to help you very much; what is the host OS and what guest are you running?  I assume Ubuntu is the guest but the host might be anything so tell us more and try removing **virtualbox-dkms** from the guest if that is what you have done; I don't think you will see any problems or difficulties if you do so.

---

