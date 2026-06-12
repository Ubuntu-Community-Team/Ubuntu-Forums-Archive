---
title: "Apache + Downloads"
date: 2014-03-16
forum: Server Platforms
---

### Post by lmao32895 on 2014-03-16
ok,  sorry if this has been answered before but i have searched google and this forum now for weeks and still can't find my answer.

I am running Ubuntu 12.04-Server and have one site located on this server using PHP. this site sells digital downloads in the form of a .zip file. my problem is that a customer can only download one zip file at a time instead of 3 or more.
please if anyone can help I would be very grateful!!

---

### Post by SeijiSensei on 2014-03-17
That's likely the way the PHP application is designed, not an Apache problem.

Does the application use a shopping cart?  Have you looked at the application's PHP code?  If you can tell where the downloads are triggered, perhaps there is a way to have the application iterate over the entries in the cart and send each file separately.

The other alternative would be to bundle the files into a single ZIP file and send that.  That would be pretty easy to program in PHP.

If you don't have control over the application's code, I don't think there is much you can do to change this behavior.

---

### Post by lmao32895 on 2014-03-17
yes we have a shopping cart and each of the 200 products are in zip files already for individual sale and download. I have talked with our PHP guy and he says its not the PHP but who knows for sure. I'll look deeper into the PHP but any other advice would be great.

Thank you

---

### Post by SeijiSensei on 2014-03-17
I think building a ZIP file that contains the other ZIPs is probably the easiest solution.

---

