---
title: "Advice on CMS selection"
date: 2010-06-21
forum: Server Platforms
---

### Post by madsporkmurderer on 2010-06-21
I'm currently in the process of overhauling the website for a JCR (essentially a student union for about 400 university students); at current we have a server that is a hideous mess- the main site runs on django with various python apps running under a subdomain, a variety of php apps just mashed onto the main domain with all-sorts of outdated crap that isn't documented.

While I have a fairly good knowledge of server admin, php and MySQL I am not very knowledgeable in the area of CMSs or content frameworks.
The number one requirement is that it is easy to maintain and doesn't take long to learn your way around; we get a new computer rep every year and abilities are variable; I am taking a guess that php/mysql is the technology that we are most likely to get knowledge of hence is a preference.
Another big requirement is ability to accept webauth and to allow accounts to be uploaded from flatfile; ability to have accounts tied to expiry dates would be nice but not essential.
Another requirement is to be as forgiving as possible of people mashing crappy code onto it; there are a collection of not exactly perfect apps that have been written as stand-alones which it is not practical to rewrite- having these on the server in an easily findable and intuitive location would be very useful.
Standard things like easily customisable looks, at least admin/editor/user roles, etc are also required.

Could you please suggest a good CMS or framework that would fit my requirements?

Thanks in advance,
Mike

---

### Post by kevin11951 on 2010-06-21
Drupal. Drupal... Oh, by the way, did I mention Drupal?  Install a few modules (very easy), and you have the greatest CMS in the world!  

(Off the top of my head) Modules:
[http://drupal.org/project/admin_menu](http://drupal.org/project/admin_menu)
[http://drupal.org/project/webform](http://drupal.org/project/webform)
[http://drupal.org/project/ckeditor](http://drupal.org/project/ckeditor)

admin menu places all admin tools at the top of every page (if you are logged in as admin)

webform lets you create simple - advanced web forms with little more than point and click.

ckeditor is a wysiwyg editor for filling out any/all text areas on your site (individual forms can be disable from its admin gui)

---

### Post by Leppie on 2010-06-21
if you know PHP and MySQL at a good level, you could try joomla as well.

---

### Post by Thirtysixway on 2010-06-21
I always recommend Drupal to clients and anyone else looking for a cms.

---

