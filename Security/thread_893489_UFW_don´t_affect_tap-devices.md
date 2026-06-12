---
title: "UFW: don´t affect tap-devices"
date: 2008-08-18
forum: Security
---

### Post by adieb on 2008-08-18
Hello

Is it possible to tell ufw not to filter any packages on a certain devices? (tap0, tap1, tapN)
Or to tell, only to care about a certain device? (eth0, eth1, eth2)

I am setting up Virtualbox-Environment with BridgedNetworking. I want to secure the Host with UFW,
but I want the VMs to have their own policies, managed by the firewall inside of themselves...

---

### Post by rgl2020 on 2008-09-02
Did you ever find out how to do this?  I would like to know too.  I'm having the same problem.  If I have UFW turned on with eth0 and tap1 bind, then I can't access the network or internet from inside vbox.

---

### Post by adieb on 2008-09-03
no, sorry, didnt´t.
did you in the meantime?

---

### Post by rgl2020 on 2008-09-04
Yeah, I found the information in the Community Documentation.

[https://help.ubuntu.com/community/KVM?highlight=(iptables)|(bridge)]("https://help.ubuntu.com/community/KVM?highlight=(iptables)|(bridge)")

This was taken from it:

iptables

Add these rules to iptables :

# allow incoming packets for kvm guest
IPTABLES -A FORWARD -d $IPADDR_FROM_GUEST_OS -j ACCEPT
# allow outgoing packets from kvm
IPTABLES -A FORWARD -s $IPADDR_FROM_GUEST_OS -j ACCEPT

Change "$IPADDR_FROM_GUEST_OS" to the actual ip address of the kvm guest (I advise you configure your guests to have a static IP address).

If you use ufw, add these rules to /etc/ufw/before.rules


I added it into my /etc/ufw/before.rules and it works great.  Make sure you remove the "IPTABLES" from the code above when you add it.  I accidently left it in and had to use safe terminal to re-edit to get back into gnome.  It caused my system to hang on boot.

---

### Post by Brewtal on 2008-09-15
rgl2020: Thank you so much! I've spent the last day trying to get this working.

---

### Post by r4e on 2009-01-04
Thanks rgl2020!

If you stick the two lines below at the end of /etc/ufw/before.rules on the host machine and disable/enable ufw it seems to work. This way you shouldn't have to invoke those iptables commands everytime you reboot.

-A FORWARD -d 192.168.1.5 -j ACCEPT
-A FORWARD -s 192.168.1.5 -j ACCEPT

Of course replace 192.168.1.5 with the static IP that you assigned to your guest OS.

---

### Post by rgl2020 on 2009-01-05
I thought that's what I said, but I guess I didn't make it clear.  Glad you got it working properly.

---

