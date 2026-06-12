---
title: "vgetty and external programs"
date: 2008-05-31
forum: Server Platforms
---

### Post by elvinatom on 2008-05-31
I setup an answering machine with vgetty on an ubuntu server 7.10 without gui. My wife relies on accessing the messages from windows, so I wrote a little script that converts the messages (.rmd-files) to wave (.wav-files) automatically. I inserted in the voice.conf "call_program /usr/bin/convert_message". After that vgetty hung up right after it picked up (without the greeting). The script did get executed instead of vgetty playing back the greeting or recording the message.

Here is my question: How do I have a script started right after a message is left (with the filename of the message + caller id as parameters $1 and $2)? Any suggestion would be greatly appreciated!

---

