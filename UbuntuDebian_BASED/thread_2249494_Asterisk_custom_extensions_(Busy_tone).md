---
title: "Asterisk custom extensions (Busy tone)"
date: 2014-10-22
forum: Ubuntu/Debian BASED
---

### Post by cky on 2014-10-22
Hello!

Im trying to write custom extension dialplan that would play custom busy sound. Im wondering becuase by default it doesnt. :/ 

So if for example im calling 01234567 and the called number is busy it has to send back to the extension that busy sound.

This is what i have for now:

```

;exten => _X.,1,Answer
;exten => _X.,n,Dial(${OUTBOUNDTRUNK}/${EXTEN:0}
;exten => _X.,n,Playtones(busy)
;exten => _X.,n,Playback(busy)
;exten => _X.,n,Busy(10)
;exten => _X.,n,Hangup
```


I really lack of experience in "customs" so please be patient with me :P

Thanks

P.S. if its not in appropriate forum i apologize

---

