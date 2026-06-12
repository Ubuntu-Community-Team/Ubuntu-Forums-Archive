---
title: "Acer Aspire Overheat Options"
date: 2011-10-04
forum: The Cafe
---

### Post by Kilz on 2011-10-04
The Acer Aspire 5738G / 5738ZG / 5738Z / 5738 / 5338 / 5536 / 5536G / 5236 have known heat issues. A search of the forums and google have helped me to overcome these issues for the most part. But there was no place that gathered all the links and info into one place. So I am posting this here to help others.

I inherited a Acer Aspire 5536 and, of course I put linux on it immediately to replace the Windows Vista that was running slow as molasses in January. But the temperature was running real hot, topping out at 80c. Here is what I did.

1. I updated the bios using a [ freedos usb stick]("http://samiux.blogspot.com/2010/06/howto-make-bootable-freedos-usb-dongle.html") and the latest bios from acer. 
2. I updated the video driver manually to the [latest ATI drivers manually]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_the_drivers_manually"). 

That got the laptop down to the 65-70c range, still to hot. 
[COLOR="Red"][SIZE="2"]The next move is not fort the faint of heart or those that lack the ability to follow directions to the letter.[/SIZE][/COLOR]

3. I disassembled the laptop  using a [pdf of the service manual]("http://www.azbooki.ru/literatura.php?name=instrukcii-po-razborke-noutbukov-acer.txt"). Cleaned the fan and the old thermal paste, then applied new thermal paste to the cpu and gpu. 

This got the laptop down to the 60c range at idle.
[COLOR="Red"][SIZE="2"]This next step is really not for those that fear change. I do not suggest everyone is capable of this step.** Do it at your own risk.**[/SIZE][/COLOR]

4. I found this thread on a forum on [air flow in the Acer Aspire line]("http://forum.notebookreview.com/acer/481690-acer-5738g-bottom-vent-built-closed.html"), and drilled out sealed air vents in the laptop case after disassembling it again. The laptop now idles at 46c and had a temp of 65c under heavy load.

---

