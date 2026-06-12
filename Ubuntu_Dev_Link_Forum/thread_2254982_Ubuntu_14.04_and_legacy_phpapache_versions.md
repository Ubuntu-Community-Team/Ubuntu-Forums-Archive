---
title: "Ubuntu 14.04 and legacy php/apache versions"
date: 2014-12-01
forum: Ubuntu Dev Link Forum
---

### Post by Gabriel_Tiste on 2014-12-01
Hi guys, I am maintaining a legacy application that we are trying to port from windows and it runs some old php/apache versions.

More exactly Apache 2.2 and PHP 5.2.6. Are there a way to run these versions in a newer Ubuntu server like 14.04?

I have scoured the net but havent found so much to help me and again, im not really a sysadmin so my knowledge is limited. But im not asking for someone to give me the total answer, but some clues how to get going.

Best regards,

GT

---

### Post by tgalati4 on 2014-12-01
First, I would find out the newest Ubuntu version that runs Apache 2.2 and PHP 5.2.6.  Install that, create a development environment and port the code to get it running.  Then try a small upgrade to the next LTS version say 12.04.  Run that for a while.  PHP is pretty good about backward compatibility.  The newer versions add new features which will not be in your legacy code.

An alternative is to run 14.04 and create a virtual machine with an older distro that just runs your legacy code.  Then create another vm with a newer version of apache and php and port from the old version to the newer version.

A third option is to keep the Windows version running and start from scratch with a new application using the latest frameworks.  The Agony Units will probably be about the same.

Trying to "[pin]("https://help.ubuntu.com/community/PinningHowto")" older versions of Apache and PHP on the latest LTS will cause problems.  It is possible--just as anything is possible in linux, but it would be problematic to use old, "pinned" frameworks on an LTS distro that expects updates of those same frameworks.

So, yes, you can do it, but I won't describe how to do it, because it is bad practice.

---

### Post by Gabriel_Tiste on 2014-12-02
Informative response, thank you. 

I will try the upgrade approach and see how its playing. I figured that latest LTS would not accept older packages due to security perspective...

Thou a total rewrite would be too time consuming at the moment, plans to do this are in the future.

Thanks for your answer.

Best regards,

GT

---

