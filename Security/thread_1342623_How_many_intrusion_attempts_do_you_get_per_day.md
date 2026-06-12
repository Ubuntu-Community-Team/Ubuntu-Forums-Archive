---
title: "How many intrusion attempts do you get per day?"
date: 2009-12-01
forum: Security
---

### Post by harry71194 on 2009-12-01
:~$ sudo iptables -nL | curl -s -F sprunge=\<- [http://sprunge.us](http://sprunge.us)
 [http://sprunge.us/gSae](http://sprunge.us/gSae) (feel free to remove this list if for some reason intruder's IPs should be kept secret)


In my opinion, that's a lot, that is only one day's worth of IPtables. I flushed it last morning, and that was the list 24 hours later.

My little security script I have, stopping people from trying to utilize my host as a proxy (not simple proxy-scans, but actually attempting to use it for bittorrent), consists of a simple crontab and PHP.
```
/sbin/iptables -F
for i in `cat /path/to/badips.txt`
do
/sbin/iptables -I INPUT -s $i -j DROP
done

```and the PHP side,
```
<?php
$foo = explode("\n",file_get_contents('/path/to/badips.txt'));
echo("Excuse me sir, what are you doing?");
if (!in_array($_SERVER['REMOTE_ADDR'],$foo)) {
 $foo[] = $_SERVER['REMOTE_ADDR'];
 file_put_contents('/path/to/badips.txt',implode("\n",$foo));
}
?>

```What are your (in)securities caused you to create, and how many of those "l33t h4xors" do you catch daily? ;)

Sorry if in wrong section, this seemed like the most relevant one..

---

