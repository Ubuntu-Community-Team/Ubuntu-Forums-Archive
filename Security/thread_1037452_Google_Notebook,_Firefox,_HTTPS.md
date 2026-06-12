---
title: "Google Notebook, Firefox, HTTPS"
date: 2009-01-11
forum: Security
---

### Post by fhsm on 2009-01-11
Random little discovery: 
I like to use the firefox addon for google notebook but it connects over http.  The customise google addon doesn't give the force to https option for notebook that it does for other google services.

I went on a little hunt to see if I could fix this problem.  

```
~/.mozilla/firefox/<longstring.defualt>/extensions/notebook@google.com/lib/gnote.js 
```

can be edited to fix this problem.  Make the file writeable, open in the editor of your choice and change the first line from

```
GNOTES_SERVER="http://www.google.com/notebook/"
```
to
```
GNOTES_SERVER="https://www.google.com/notebook/"
```

a quick trip to wireshark will confirm that you are running over ssl now.

Of course your mileage may vary.  Best not to keep anything to impt in google notebook but nice to use ssl when it's there.

---

