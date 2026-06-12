---
title: "Updated Server -Lost the ability to see shares"
date: 2009-08-06
forum: Server Platforms
---

### Post by roystreet on 2009-08-06
Hello -I've been successfully using ubuntu server for a few months now and it has been incredibly reliable.  I'm still a newbie.  It has been telling me that there were updates ready for it.
Today I went ahead & updated my server remotely via the terminal by:
```
sudo apt-get upgrade
```

During the install process it asked if I wanted to update the samba config file & I said no.  I rebooted after it was done. Now I can still log into via terminal just fine and dandy, but now I can't see it via nautilus and I'm sure it's not visible via windows explorer in my windows machine.  Any ideas here?

Also, is there a way to undo updates?  I might want to do that.

Thanks
~roystreet

---

### Post by roystreet on 2009-08-06
Just let you know what I've tried and to clarify:
[LIST]
[*]the server doesn't show up in the network at all
[/LIST]
1) I have checked via webmin that the config file is the exact same as before, so it was not "wiped out"
2) I stopped the samba server & then restarted it.

None of this caused the server to show back up.

Help!

~roystreet

---

### Post by roystreet on 2009-08-08
OK, I just tested it from a windows machine.  The windows machine can see the server just fine, so this adds an extra twist to it.  Anyone have a guess of why a linux machine can't see a linux server, but a windows machine can?  I thought it had to do with the update to my server, but maybe it has to do with something I did on my linux desktop.

This isn't exactly what I was looking for, but it's a challenge.

Thanks,
roystreet

---

### Post by Thirtysixway on 2009-08-08
Is your server using DHCP for its IP address?  Try accessing it via IP if you're doing it by hostname.  If that doesn't work, verify the IP by pinging it with the windows computer.

---

### Post by roystreet on 2009-08-08
Thirtysixway, I'm not sure why...Guess what it's working now. :):-k  I pinged it & it responded every time also.  This was the first time I tried to connect to it since I had checked it with windows.  I don't know why that would make a difference though?  I'm not sure if pinging it did anything?  I could browse to the webmin webpage on it, I also could log into it via ssh terminal connection.  So it knew it was there?  Very odd, but as long as it keeps working - I'm happy.

~roystreet

---

