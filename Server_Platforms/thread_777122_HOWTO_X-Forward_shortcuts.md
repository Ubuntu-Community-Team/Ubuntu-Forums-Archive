---
title: "HOWTO: X-Forward shortcuts?"
date: 2008-05-01
forum: Server Platforms
---

### Post by Jeztastic on 2008-05-01
Hi,

As discussed on a previous thread, I am using X forwarding to start applications such as synaptic and Firefox on my server machine. Is there any way to put icons on my client desktop which will automatically do this without using cli?

Starting to hit my stride with this whole linux thing! :guitar:

---

### Post by HermanAB on 2008-05-01
Write a little script in /usr/local/bin to connect and run the application.  Make it executable and then right click on your desktop to make 'Link to an Application' or some such to the script.

---

### Post by Jeztastic on 2008-05-01
How or where could I go about finding such scripts?

Or learning how to write them? Could I just put this: ```
ssh -X jez@server firefox-3.0
``` in a file and then it would run it, or is there more to it?

thanks

---

### Post by HermanAB on 2008-05-01
Yup.  You could even put that one liner directly in a .desktop link.

---

