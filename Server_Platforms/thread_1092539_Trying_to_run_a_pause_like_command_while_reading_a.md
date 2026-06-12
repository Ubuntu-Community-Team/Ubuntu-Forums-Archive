---
title: "Trying to run a pause like command while reading a file"
date: 2009-03-10
forum: Server Platforms
---

### Post by etechship on 2009-03-10
so I have two problems.

1) The below script will read every line, except the last one. So, I added a blank line below everything.

2) I would like it to pause each time it has a line, and it doesn't

here is my code:
```
#!/bin/sh

##growisofs -Z /dev/cdrw -dvd-video $file/

curl -s "http://admin.ucstreaming.net/_operations/dvd.php?status=burn" |
while read line; do
	read -p "press enter to continue"
	echo "key pressed"
done
```

---

