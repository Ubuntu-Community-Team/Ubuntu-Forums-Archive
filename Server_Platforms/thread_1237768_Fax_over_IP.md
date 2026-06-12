---
title: "Fax over IP?"
date: 2009-08-11
forum: Server Platforms
---

### Post by IrishWristwatch on 2009-08-11
I currently am experiment with Ubuntu Server.  I have a CUPs server fully installed and a printer already configured with the computer.

What do you guys recommend I do to setup the computer as a sort of crude fax server?  The setup doesn't have to be anything fancy, but is there any way make it send and receive faxes over the internet, then send them through my PCI fax modem on the box to a physical fax machine?

Any input will be appreciated, thanks.

---

### Post by Vegan on 2009-08-11
You are probably going to have to "roll your own" as I have searched for FAX programs for a long time for internal purposes.

I have looked at using a form to upload a document then use a rasterizer to send it out the fax card to a recipient. There is fax software so rasterizing is not hard to implement.

The main problem is dealing with the various document types that potentially will be done.

The other direction, recieving a fax is fine, then emailing it as an attachment can cure that problem. :mrgreen:

This is nominally what you will need, so a little web development and a little PHP should be all you need. :)

Recieved faxes need to be OCRed if you have multiple recipients as you need to read the "to" area of a standard fax cover sheet. :confused:

So depending on the complexity the code is easy to daunting. :lolflag:

Trying to use low level facilities will be far more complicated.

---

