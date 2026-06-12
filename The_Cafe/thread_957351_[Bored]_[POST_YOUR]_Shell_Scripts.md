---
title: "[Bored] [POST YOUR:] Shell Scripts"
date: 2008-10-24
forum: The Cafe
---

### Post by Noxn on 2008-10-24
I am bored, and wanted to see some of the scripts Ubuntu users make.

I did some, but one of my best is this: (I am still learning)

```
#!/bin/bash
#This little script pings google, and if it is a succes, musik will play to inform you that the internet is working.
#AND IT WILL BEEP :D
#IMPORTANT:::
# CHANGE THE MUSIC; OR IT WONT WORK!

#---Functions---
fail() {
trys=$trys+1
echo "Ping to google FAILED"
echo "Internet connection either (really) slow, or non-existant"
echo "Retry in 20 seconds"
sleep 20
main
}

succes() {
echo "SUCCES!"
echo "Number of fails: $trys"
cd ~/Music
#Change here-------------Requires Mplayer, or you could use totem.
mplayer Crying_Soul
exit
}

main() {
echo "Trying to ping WWW.GOOGLE.COM, Timeout in 20 seconds"
echo "Sending 5 times, Need all 5 in 20 second or fail"
ping -c 5 -w 20 -a  www.google.com || fail
succes 
}

#---I/O---
trys=0
main
```

I made this today becouse my internet wasn't working for a while, so this pings google until it works. Got the idea from a post around here.

Post your Shell Scripts (if you want to)



But i think this thread will die in like 10 seconds.


EDIT: Does a thread like this already exist? if yes then post a link Please.

---

