---
title: "configure plymouth theme?"
date: 2010-10-18
forum: System76 Support
---

### Post by ranch hand on 2010-10-18
Having gone through 10.04 and 10.10 testing you might think I would know this.   I do not as plymouth will not work on my box.

I got my wife the Pangolin with 9.10 on it so that she could use it until the LTS came out.  Just upgraded to it as I am scared of it as it will not work on my box.

Works fine on the Pang.

I do want to change from the ubuntu-text to ubuntu-logo plymouth theme.  I have not got a clue.  All I know is that it is a simple CLI command.

If some kind soul could be of some help it would be greatly appreciated.

---

### Post by isantop on 2010-10-19
If you're getting the ubuntu-text theme in plymouth, chances are it's because your system is having a hard time running the ubuntu-logo theme, probably due to a proprietary drivers issue. I'd say your best bet would be to follow the directions here: [http://knowledge76.com/index.php/Fixing_Bad_Plymouth_Resolution](http://knowledge76.com/index.php/Fixing_Bad_Plymouth_Resolution) I believe that should get you going just fine.

---

### Post by ranch hand on 2010-10-19
Thanks for your reply.

I was actually after the command to change themes but your reply was of more use.

Did not have ubuntu-logo theme installed.

I just edited the default theme script and ran update-initramfs -u.

Theme looked horrid.  Then I found your reply and now every thing is fine.  Thanks again.

---

