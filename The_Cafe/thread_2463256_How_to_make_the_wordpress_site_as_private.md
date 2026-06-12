---
title: "How to make the wordpress site as private"
date: 2021-06-07
forum: The Cafe
---

### Post by satimis on 2021-06-07
Hi all,

Is there an easy way to make WordPress site a private site without plugin?

My requirement is simple;
Only registered users can login with password to browse the site, all pages.
New user can make a request on email and if approved, I'll email the password to him/her

If a plugin is required please recommend an appropriate one.  There are many plugins on Internet for this function.

Thanks

Regards

---

### Post by mIk3_08 on 2021-06-07
Just make a login portal page as your front-page or landing page going to the system website when successfully login in.
A portal page that say's this is your website plan. Please login. 
This front-page must be securely protected. there are a lot of web security software that can help protect your website.
security is very important to your plan so that no leakage link to the web system you are planning.

---

### Post by satimis on 2021-06-07
> **mIk3_08 said:**
> Just make a login portal page as your front-page or landing page going to the system website when successfully login in.
A portal page that say's this is your website plan. Please login. 
This front-page must be securely protected. there are a lot of web security software that can help protect your website.
security is very important to your plan so that no leakage link to the web system you are planning.

Hi,

Thanks for your advice.

On Google search I found following document;
How to Create a Client Portal in WordPress
[https://www.wpbeginner.com/wp-tutorials/how-to-create-a-client-portal-in-wordpress/](https://www.wpbeginner.com/wp-tutorials/how-to-create-a-client-portal-in-wordpress/)

Would it be relevant for me to follow its steps?

Besides it still needs following plugin;
**The &#8220;All-In-One&#8221; Membership Plugin for WordPress**
[https://memberpress.com/](https://memberpress.com/)

It is available in WP "Add" plugin
**"All in One SEO &#8211; Best WordPress SEO Plugin &#8211; Easily Improve Your SEO Rankings"**

Please advise.  Thanks

Edit:
The running security plugin - wordfence

Regards

---

### Post by SeijiSensei on 2021-06-07
Any reason why this has to happen in software and not through the basic authentication mechanism built into Apache?

[https://httpd.apache.org/docs/2.4/howto/auth.html](https://httpd.apache.org/docs/2.4/howto/auth.html)

---

### Post by satimis on 2021-06-07
> **SeijiSensei said:**
> Any reason why this has to happen in software and not through the basic authentication mechanism built into Apache?

[https://httpd.apache.org/docs/2.4/howto/auth.html](https://httpd.apache.org/docs/2.4/howto/auth.html)
Hi,

Thanks for your advice.

What I expect to achieve are as follows:
1. Only authorized users can login the site with user ID and password to visit the site, all pages.  This notice is displayed on the HOME page.
2. New users can make request with the expected user ID and I'll email them the password if approved.    This notice is also displayed on the HOME page with a click for making request.

Please advise how to make it on Apache?  Thanks

Edit
===
It is a WordPress site hosted on HostGator

Regards

---

### Post by SeijiSensei on 2021-06-08
You could have a landing page separate from the WP installation that explains how to obtain a password. Probably should have a mailto: URL that people can use to request the password.

Then on the same page have a link to the WP site using basic authentication as shown in the document I linked to.

If you expect to have a lot of validated users, then using .htpasswd files might require too much work. Basic auth can use other authentication mechanisms like [SQL queries]("https://httpd.apache.org/docs/2.4/mod/mod_authn_dbd.html").

---

### Post by satimis on 2022-02-17
> **SeijiSensei said:**
> You could have a landing page separate from the WP installation that explains how to obtain a password. Probably should have a mailto: URL that people can use to request the password.

Then on the same page have a link to the WP site using basic authentication as shown in the document I linked to.

If you expect to have a lot of validated users, then using .htpasswd files might require too much work. Basic auth can use other authentication mechanisms like [SQL queries]("https://httpd.apache.org/docs/2.4/mod/mod_authn_dbd.html").
I'm very surprised that your advice just arrived to me.

What I expect to achieve is;
1. Only the visitors can browse my websites with password sent to them by me.
2. Other visitors without password only browse a blank website with notice saying "This is a private website ......."

Regards

---

### Post by kevdog on 2022-02-17
So not to complicate your demands, but stick a reverse proxy in front of your wordpress site and then add something like authelia which does the authentication [https://github.com/authelia/authelia](https://github.com/authelia/authelia).  There are other similar projects -- is this going to increase the complexity of your authentication as compared to .htaccess files -- yep! -- just depends how you want to spin it.

---

### Post by #&amp;thj^% on 2022-02-17
> **SeijiSensei said:**
> You could have a landing page separate from the WP installation that explains how to obtain a password. Probably should have a mailto: URL that people can use to request the password.

Then on the same page have a link to the WP site using basic authentication as shown in the document I linked to.

If you expect to have a lot of validated users, then using .htpasswd files might require too much work. Basic auth can use other authentication mechanisms like [SQL queries]("https://httpd.apache.org/docs/2.4/mod/mod_authn_dbd.html").

+1 I like it. :) a little more complex but worth the effort.

---

