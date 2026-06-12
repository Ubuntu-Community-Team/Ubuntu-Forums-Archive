---
title: "Get into locked desktop to shutdown"
date: 2012-02-19
forum: Security
---

### Post by Morat on 2012-02-19
My daughter has left herself logged into the machine and gone to sleep and I need to shut it down.

I could just go ahead and do so but she may lose information. I can 'su' to her on the command line but I know she has at least one OpenOffice spreadsheet running so ideally, I need to get to her desktop to close and save it. Any suggestions how to do this?

Or can I get to the OO process through ps and send it some close-and-save signal from the command line?

Morat.

---

### Post by winh8r on 2012-02-19
Sorry I cannot give a surefire answer, but I do know that the default "auto-save" function on open office is 15 minutes!

So if your daughter has been asleep for an hour then it should have auto saved everything by now , and you could probably shutdown using the shutdown -h +20 which would bring it to a halt in 20 mins thereby allowing another 15 mins for an autosave after the command is run.

Bit of weird thinking maybe, but I am sure that between autosave and open office auto recovery the document should be fairly safe

(**imaginary disclaimer goes here!)

---

### Post by Morat on 2012-02-19
Fair enough. It should be fine then since she has been asleep a couple of hours now. If she does lose anything she feels is improtant, then hopefully it will help to teach her about saving and closing stuff down when she has finished in future.

Thanks for the reply.

---

