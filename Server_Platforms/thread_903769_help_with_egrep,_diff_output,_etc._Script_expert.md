---
title: "help with egrep, diff output, etc. Script expert"
date: 2008-08-28
forum: Server Platforms
---

### Post by inphektion on 2008-08-28
I have this thread [here.]("http://ubuntuforums.org/showthread.php?t=898110")
This is sort of a continuation or a further change.  
The script is sending me emails about an upload or download when one didn't occur.  Basically I have an ftp xferlog being watched by incron and when it gets accessed and closed this script runs to notify me when a specific user does an upload or download:
```

[ -f /root/script/johnny_ftpU.latest ] || touch /root/script/johnny_ftpU.latest
[ -f /root/script/johnny_ftpD.latest ] || touch /root/script/johnny_ftpD.latest

tail -n50 /var/log/xferlog | egrep "\<i\>.*\<johnny\>" > /root/script/johnny_ftpU.recent
tail -n50 /var/log/xferlog | egrep "\<o\>.*\<johnny\>" > /root/script/johnny_ftpD.recent
diff -a -N /root/script/johnny_ftpU.latest /root/script/johnny_ftpU.recent > /root/script/johnny_ftpU.new
if [ "$?" -gt "0" ]; then 
        mail -s "Johnny FTP UPLOADED files..." "me@mycompany.com" < /root/script/johnny_ftpU.new
        mv /root/script/johnny_ftpU.recent  /root/script/johnny_ftpU.latest
fi
diff -a -N /root/script/johnny_ftpD.latest /root/script/johnny_ftpD.recent > /root/script/johnny_ftpD.new
if [ "$?" -gt "0" ]; then
        mail -s "Johnny FTP DOWNLOADED files..." "me@mycompany.com" < /root/script/johnny_ftpD.new
        mv /root/script/johnny_ftpD.recent  /root/script/johnny_ftpD.latest
fi

```

Unfortuneatley i can't do two sep scripts cause you can only have one path in incrontab to act on at a time which for me is /var/log/xferlog.  
But now with any access to the xferlog I'm getting old upload or downloads for johnny.

---

### Post by inphektion on 2008-08-30
I cleared te xferlog and it helped a bit but now seems to send too many emails when a download occurs... weird, if any one sees any way to improve the above pls let me know.

---

