---
title: "CourierSMTP, ClamCour filter and ClamAV"
date: 2008-04-29
forum: Server Platforms
---

### Post by stego_s_aurus on 2008-04-29
Hello all!
  I'm having a rather advanced problem and I cannot seem to find any help on how to deal with it:

We use CourierSMTP for our mail transport, and we use ClamCour to have Courier pass along messages to ClamAV for scanning.

Our problem is that there are newsletters that are being sent out from our marketing company to people In our company that are being reported as "Signature is Phishing.Heuristics.Email.SpoofedDomain": We are aware that the email company is mailing as us, and we do have their servers included in our spf record.

I'm trying to determine if there is a way to tell Courier to NOT send messages that come from this one specific server through the filter.

Thanks for any help!

-Stego

---

