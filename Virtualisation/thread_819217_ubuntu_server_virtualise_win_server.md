---
title: "ubuntu server virtualise win server"
date: 2008-06-05
forum: Virtualisation
---

### Post by Mr_Whippy on 2008-06-05
Hi all,

just a quick query really and i think i already know the answer but wanted to check before i did any of the work and found i was completley wrong,

the question is, if i run a virtual machine on ubuntu server, (cli only) and install windows server on it, then can i still rdp, vcn onto the win virtual machine and get the GUI.

probably a silly question with an obvious answer but wanted to be sure.

thanks.

---

### Post by .nedberg on 2008-06-05
Yes, you can!

---

### Post by Mr_Whippy on 2008-06-05
Thanks i thought so, just was not sure,

---

### Post by bradmkjr on 2008-06-05
What you end up doing is using the VMware Server Console on a second computer. This application talks to the VMware server over the network, and displays the Virtual Machine Screen on the client computer, even though there is no gui on the Server. This is a common setup and works really well. Once you have Server installed feel free to go ahead and run RDP, as that is more optomized for lower bandwidth and you will see better overall performance compared to the standard VM Console.

Good Luck,
Bradford Knowlton
[http://x86v.com](http://x86v.com)

---

