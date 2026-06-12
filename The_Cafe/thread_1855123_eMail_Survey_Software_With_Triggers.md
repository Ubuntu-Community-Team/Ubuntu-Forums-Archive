---
title: "eMail Survey Software With Triggers"
date: 2011-10-05
forum: The Cafe
---

### Post by t4thfavor on 2011-10-05
Hi All,

I am currently looking for a piece of software that will allow sending email's to customers when certain events occur.

It is for a pharmacy, so the events will contain things like:

First dispense, Second Dispense, Shipments, Shipment delays, time passing, etc.

The software should allow participants to opt out via a link if possible.

I know of several projects like PHPList, and OpenEMM, but those products appear to only support list based mailings.

Needless (or not) to say here in the US a hosted solution is out as I am governed by HIPAA.

We are currently working with some in-house solutions, and with some expected volume increase I was wondering if there was something more commercial(paid or other) that would satisfy this request.

I have also been looking at modifying phplist to allow our in-house systems to insert addresses, and lists, delete list associations, etc when the above events occur.

Thanks!

---

### Post by t4thfavor on 2011-10-06
I'm only going to bump this once as it appears that this type of thing may be custom only.

Thanks,

---

### Post by SeijiSensei on 2011-10-06
I, or someone like me, could write this in PHP with a backend database, but it would be a custom job.  I doubt there's anything out there that will meet your specific needs.  

Having just finished an online appointments system for a healthcare provider, it requires some careful design to conform to HIPAA regulations.  You can't, for example, say anything in the e-mail about the type of drugs involved, or even the prescribing physician.  (Imagine, for instance, a message prescribing tamoxifen that is intercepted by an employer.)  The appointments system I developed sends the patient an email containing only an https link back to the web site.  The patient needs to log in to read the actual message.  That's pretty common on other systems for patient communication that I've seen.

Of course all the patient information needs to be encrypted, preferably with AES256, before being stored in the database.

---

### Post by t4thfavor on 2011-10-06
> **SeijiSensei said:**
> I, or someone like me, could write this in PHP with a backend database, but it would be a custom job.  I doubt there's anything out there that will meet your specific needs.  

Having just finished an online appointments system for a healthcare provider, it requires some careful design to conform to HIPAA regulations.  You can't, for example, say anything in the e-mail about the type of drugs involved, or even the prescribing physician.  (Imagine, for instance, a message prescribing tamoxifen that is intercepted by an employer.)  The appointments system I developed sends the patient an email containing only an https link back to the web site.  The patient needs to log in to read the actual message.  That's pretty common on other systems for patient communication that I've seen.

Of course all the patient information needs to be encrypted, preferably with AES256, before being stored in the database.


I am Supervisor of Software Dev, about a 25 man team. We can do it too, I was just making sure that there is nothing that fits the bill before we go about reinventing this wheel as we have lots of other stuff to do.

Thanks for the offer.

---

