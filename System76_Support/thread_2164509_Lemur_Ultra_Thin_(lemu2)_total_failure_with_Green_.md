---
title: "Lemur Ultra Thin (lemu2) total failure with Green Switchs."
date: 2013-07-31
forum: System76 Support
---

### Post by houstonbofh on 2013-07-31
I have an older Lemur Ultra Thin that up to now I have been very happy with.  (And have posted my happiness with it here more than once)  However, I just discovered a new problem with D-link Green switches.  No link. Ever...  If you force 100BaseTx-FD it will link, but not properly pass traffic.  An article about this issue is here. [http://askubuntu.com/questions/311517/how-do-i-connect-to-an-energy-efficient-ethernet-enabled-switch](http://askubuntu.com/questions/311517/how-do-i-connect-to-an-energy-efficient-ethernet-enabled-switch)

Now this laptop is probably out of warranty.  (It is about 3 years old)  But it is a manufacturing defect, so I am wondering if there is some type of recall program for this nic...

Thanks.

---

### Post by isantop on 2013-07-31
No, we only ever used those NICs in the LemU2, PanP6 and PanP7 laptops. It's a hardware issue, they just will not connect to those specific switches. We haven't been able to confirm whether it's the switch or the NIC, but there's nothing we can do to fix it.

---

### Post by houstonbofh on 2013-08-02
It was on two different models of dlink green switches... And in that link I posted it references this in the FreeBSD jmicron driver.
> If the full mask revision number of JMC25x controller is less than or equal to 4 and link partner enabled IEEE 802.3az Energy Efficient Ethernet feature, the controller would not be able to establish a 1000baseT link. Also if the length of cable is longer than 120 meters, controller can not establish a 1000baseT link. The known workaround for the issue is to force manual link configuration with 100baseTX instead of relying on auto-negotiation.
And I do have the rev3 of that card, so it is likely a hardware bug.  And I am understanding that an upgraded motherboard with a newer chip was never created, correct?

---

### Post by isantop on 2013-08-02
It's not. We switched to Realtek controllers after that.

---

### Post by isantop on 2013-08-02
It's not. We switched to Realtek controllers after that.

---

### Post by golfdiesel on 2013-08-03
The Realtek controllers seem to do a much better job. I have however seen issues with them as well in the past (5+ years ago). I switched to a gbit network at home and whatever I did the Realtek controller would refuse to connect at 1 gbit. I switched to an Intel controller and it worked immediatly. They are more expensive but usually Intel controllers work without problems in 99% of the cases.

---

### Post by houstonbofh on 2013-08-04
When given the choice, I go with Intel as well.  Less load on the CPU...  And some of the RealTek nics can not do 9000 mtu jumbo frames.  They have issues over 6000.  But they do work on green switches. :)

So, do you have a trade up program? :D
(It's worth a shot)

---

### Post by isantop on 2013-08-05
No trade up program, but you can donate your old computer.

---

### Post by golfdiesel on 2013-08-06
Is it a home switch or is it a managed switch in an office environment? In a home environment I would change the switch out.

---

### Post by houstonbofh on 2013-08-08
I am a hired gun network professional, and it is my work laptop.  It looks bad when I get to a client and can not use my laptop...  But I can't get them all to change switches.  However, I have had a few "reconsider" green switchs, as I am not the only thing with issues with them.

---

