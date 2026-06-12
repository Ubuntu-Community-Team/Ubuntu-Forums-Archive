---
title: "Firestarter fail in boot log"
date: 2010-10-20
forum: Security
---

### Post by ianc1 on 2010-10-20
I've been using Firestarter for a while and have used it to set-up inbound and outbound policies (which are probably way too restricitve) but since turning on boot logging the other day I have noted that the boot log contains the message:
```
* Starting the Firestarter firewall...                                        [fail]
```I find this somewhat alarming.

I have seen post [http://ubuntuforums.org/showthread.php?t=1568376&highlight=firestarter](http://ubuntuforums.org/showthread.php?t=1568376&highlight=firestarter) (although have not added it the auto startup list and do not wish to have it start without the root password).  What I would like to know is as the computer boots up does it set the iptables to their last setting irrespective of whether firestarter starts or does firestarter need to start to set the iptables and therefore my policies?

Any advice on whether I need to worry about this would be much appreciated.

---

### Post by cariboo on 2010-10-20
If you get that error, just open a  terminal and type:

```
sudo iptables -L
```

to list the rules. If i remember correctly the firewall rules stay in effect even if firestarter isn't running. If you see a whole list of rules, you have nothing to worry about.

I personally feel that using firestarter is a bad choice, because aside from a few bug fixes the maintainer applied, there hasn't been any development on it since 2005. Firesarter is meant to be started to apply the firewall rules, then you can pretty well forget about it.

People that run it all the time are putting themselves at risk, because it has to be run as root.

---

### Post by ianc1 on 2010-10-21
Thanks cariboo907.  I don't leave firestarter running I tend not to have it open with using the PC for the reasons you stated, which is one of the reasons the error confused me as I have not asked firestarter to open at start-up.

As I don't really understand iptables (more homework on networking and iptables) can I assume that if I compare the output of iptables -L at reboot and then after starting firestarter and find they are the same that all is OK.

The reason I chose firestarter is for its simplicity I did try Guarddog but found it a little confusing.  Can you recommend anything better.  I assume the best option is to learn iptables and do it the hard way but that could be some way off and I have no desire to cut my internet access until then.

Thanks

Ian

---

