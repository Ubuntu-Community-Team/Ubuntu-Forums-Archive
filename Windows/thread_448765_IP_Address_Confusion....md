---
title: "IP Address Confusion..."
date: 2007-05-19
forum: Windows
---

### Post by user1397 on 2007-05-19
EDIT: I figured this out now. The command systeminfo is only available in windows xp professional. to access the same info in xp home, you would have to go to accessories > system tools **or** type msinfo32 in start > run to open that same GUI window.

- - - - - - - - - - - - - - - - - - - - - - - - -

I am really confused about this whole IP address business.

For one, I have a DHCP-assigned IP address (something like 192.168.1.100)

But then, I have the type of IP address like the one they give you on this website:  [URL="http://whatismyipaddress.com/"]http://whatismyipaddress.com/
[/URL] 
I don't know what that one means, nor do I know how to find it on a **windows **computer in any sort of official way...

---

### Post by ola on 2007-05-19
The IP-address you are assigned from your DHCP-server (192.168.1.100) is the IP-address for you local network (you are probably behind a firewall/router).

The IP-address you receive when you surf to the website is your external IP-address ("Internett IP-address).

If you use the command ifconfig (not ipconfig as in Windows) you will see something like:

inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0

Hope that helps!

---

### Post by user1397 on 2007-05-20
> **ola said:**
> The IP-address you are assigned from your DHCP-server (192.168.1.100) is the IP-address for you local network (you are probably behind a firewall/router).

The IP-address you receive when you surf to the website is your external IP-address ("Internett IP-address).ah, ok, now I understand this concept.

> If you use the command ifconfig (not ipconfig as in Windows) you will see something like:

inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0

Hope that helps!Perhaps you did not understand that this is a windows discussion sub forum, so I meant **ipconfig **as in the dos prompt of windows xp, **not** the command **ifconfig **in linux.

---

### Post by kvonb on 2007-05-20
> **ubuntuman001 said:**
> ah, ok, now I understand this concept.

Perhaps you did not understand that this is a windows discussion sub forum, so I meant **ipconfig **as in the dos prompt of windows xp, **not** the command **ifconfig **in linux.

The guy just helped you out and you come back at him with attitude!

Perhaps you don't understand that "windows discussion" does not imply "Windows help and support"!

---

### Post by user1397 on 2007-05-20
> **kvonb said:**
> The guy just helped you out and you come back at him with attitude!

Perhaps you don't understand that "windows discussion" does not imply "Windows help and support"!
Actually, I did not mean to be rude, nor do I still see how I was being rude.

The "so" in my sentence can pass as a symbol for a friendly conversation, and I only highlighted words to get the key words out.

---

### Post by user1397 on 2007-05-21
bump

---

### Post by LaRoza on 2007-05-21
In the command prompt, in Windows, type "systeminfo" to get your IP address, and other info.

---

### Post by user1397 on 2007-05-21
> **LaRoza said:**
> In the command prompt, in Windows, type "systeminfo" to get your IP address, and other info.hmm...when I tried that, it just said "'systeminfo' is not recognized as an internal or external command, operable program or batch file."

---

### Post by smoker on 2007-05-22
hi,

maybe it is the 'netstat' command you are looking for, some info here:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/netstat.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/netstat.mspx?mfr=true)

best of luck

---

### Post by LaRoza on 2007-05-22
> **ubuntuman001 said:**
> hmm...when I tried that, it just said "'systeminfo' is not recognized as an internal or external command, operable program or batch file."


It works on XP and Vista, this is the schools computer. (You can't see the IP address because it is at the bottom)

edit - XP Pro, for those reading this

---

### Post by user1397 on 2007-05-22
> **LaRoza said:**
> It works on XP and Vista, this is the schools computer. (You can't see the IP address because it is at the bottom)hmmm, this is beginning to sound real strange to me, cause it still does not work.

I see that clearly you executed the command on a windows xp computer (so I'm not saying your proof is false), and I also found this: [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/systeminfo.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/systeminfo.mspx?mfr=true)

So now I've started to think that it's a windows xp pro only thing.  do you have xp pro or home?

---

### Post by user1397 on 2007-05-22
Ah, I figured this out now.  The command systeminfo is only available in windows xp professional.  to access the same info in xp home, you would have to go to accessories > system tools or type msinfo32 in start > run to open that same GUI window.

---

### Post by LaRoza on 2007-05-23
> **ubuntuman001 said:**
> hmmm, this is beginning to sound real strange to me, cause it still does not work.

I see that clearly you executed the command on a windows xp computer (so I'm not saying your proof is false), and I also found this: [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/systeminfo.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/systeminfo.mspx?mfr=true)

So now I've started to think that it's a windows xp pro only thing.  do you have xp pro or home?


I know it's resolved, but it the screen shot is the school computer XP Pro, and I use it at home on Vista Home Premium.

---

### Post by user1397 on 2007-05-23
> **LaRoza said:**
> I know it's resolved, but it the screen shot is the school computer XP Pro, and I use it at home on Vista Home Premium.k, thanks for the confirmation.

---

### Post by user1397 on 2007-05-29
bump

---

