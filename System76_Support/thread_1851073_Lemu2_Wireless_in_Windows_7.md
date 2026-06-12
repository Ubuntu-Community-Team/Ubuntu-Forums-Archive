---
title: "Lemu2 Wireless in Windows 7"
date: 2011-09-27
forum: System76 Support
---

### Post by LibertyShadow on 2011-09-27
Hey folks. First, I just want to say how happy I am with my Lemur Ultrathin. Great show. Ubuntu runs like a dream, but I really do need Windows from time to time. So I popped in my Windows 7 x64 DVD last night and got started. Unfortunately, my wireless just doesn't want to work.

I went with the intel wireless option, which turned out to be Intel Centrino Advanced-N 6200 (according to lspci). It appears the [knowledge76 article]("http://www.knowledge76.com/index.php/LemU2") link to "Intel Wireless" is actually a Realtek driver. So I went to Intel's website to get the driver, and ended up [here]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=20123&ProdId=3200&lang=eng&OSVersion=Windows%207%2C%2064-bit*&DownloadType=Software%20Applications"). Naturally, I first attempted the installer that just includes the driver. When that seemed to fail, I went with the Proset wireless bundle.

After the install completed, I rebooted, and the Proset tool said it found no supported wireless cards. I looked at the device manager, and I see a device with an alert called "Network Controller" and no Intel Wireless. Has anyone else experienced this issue?

This is probably the wrong place to look for Windows support... but I can't stand scavenging Microsoft's website for even a scrap of useful information 8-)

**Edit:** I just wanted to add that I am only getting SATA II speeds on my SATA III SSD. My hunch is that there's a SATA II controller on the motherboard. Quite unfortunate.

---

### Post by LibertyShadow on 2011-09-29
I installed the S31xx Intel Wireless drivers from [CLEVO's website]("http://www.clevo.com.tw/en/e-services/download/ftpOut.asp?Lmodel=S3100%2FS3100M%2FS3101&ltype=9&submit=+GO+") and it's working now. Marking as solved, but you guys ought to update the link on knowledge76.

---

