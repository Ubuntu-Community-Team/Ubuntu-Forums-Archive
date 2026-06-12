---
title: "Sending email from an ubuntu server without using personal account..."
date: 2011-06-25
forum: Server Platforms
---

### Post by fizgig on 2011-06-25
So I set up ubuntu server for a couple of people and I want it to be able to email them and me when it needs to.

For myself, I've done the setup where ubuntu sends email through my gmail account but for these other installations, I don't want to use my personal email address.

I do own a domain hosted by lunarpages that I don't mind using if it helps.  The email could come from [email]support@my_special_domain.com[/email] or something.

Is it possible to get that to work without ever worrying about their ISPs blocking the email (port 25)?  Is there a reliable way to do this?

---

### Post by Paddy Landau on 2012-07-05
You have various options to send emails.

If each user's server's ISP allows it, just send the emails using that ISP's SMTP. Test it. If it works, that's cool. Some ISPs will allow it, and others will not.

Another option is to use a hosting company for emails. There are some ultra-cheap ones for email-only, especially if you are sending occasional, low-volume emails, as it sounds as though you want to do.

What about the company that is currently hosting your current set-up, Lunarpages? Surely that host allows you to send emails? This would be my preferred option, as it clean, and easy to maintain and control.

Finally, you could add your new email address to GMail and send though GMail. Be aware, though, that such a method could expose your personal GMail address to the recipients — so you could create a new GMail account just for the purpose (though check with GMail's T&C whether or not that would be allowed).

---

