---
title: "Looking for a php script"
date: 2008-01-29
forum: The Cafe
---

### Post by PartisanEntity on 2008-01-29
I'm looking for a php script that does the following:

You enter your data and then it sends you an email with a link to an online invoice which has the order date and a number.

Anyone know of any free scripts that do this?

Thanks very much

---

### Post by frup on 2008-01-29
maybe some shopping cart software snippets. By itself it sounds very easy, just simple use of the mail function with a variable containing the invoice number in markup plus a database call of some sort to store the invoice.

---

### Post by PartisanEntity on 2008-01-30
> **frup said:**
> maybe some shopping cart software snippets. By itself it sounds very easy, just simple use of the mail function with a variable containing the invoice number in markup plus a database call of some sort to store the invoice.

Well, easier said than done, for someone who can't code :)

---

### Post by LaRoza on 2008-01-30
> **PartisanEntity said:**
> Well, easier said than done, for someone who can't code :)

To what extent does this have to been done and how secure? I am sure I could whip up a quick solution to it, but for real security, you'd have to get someone with more experience in such things.

---

### Post by PartisanEntity on 2008-01-30
I'll post back when I know more, it's for a friend and since I have some basic knowledge of PHP and MySQL I thought I would find some free script to install for him. I didn't want to waste anyone's time and effort with having to code it from the ground up.

At the moment I think it should be quite simple, but I have no idea what he needs exactly, just thought I would do the research in advance and see what's available out there. Thanks very much for the other though.

---

### Post by WorldTripping on 2008-01-30
The sending of the mail by the server is pretty straightforward.

The security aspect would be more complex.

i.e.

Verify and transmitting the initial client data correctly and securely.

The ability of the database to incorporate this new information correctly, and take an appropriate action.

Redirect the user to a secure area of the server where database information can be viewed.

All of the above will require knowledge of the explicit server certificates and database structure.

I don't think this is something that you could grab from say, phpfreaks.com

On the plus side, if you do build it you'll get a good insight into Apache, SSL, SQL and php.

p.s. Do some reading up on SQL injection techniques before you start coding the SQL connections.

Good Luck.

;)

---

### Post by soapytheclown on 2008-01-30
php isnt difficult i picked it up in about a week with no real programming experience since HTML isnt considered a programming language by most theres a serise of books i always find helpful when learning something new the visual quickstart range, the php one by larry ulman has an example similar to what you're after prehaps you should try learning it :D

---

### Post by frup on 2008-01-30
If you search mail() on php.net you can find everything about that function. The most simple form, and I don't mean secure, form of this script would mail to a given email address the values of the form. In the way I think the invoice number would be server side. << there you wan't ssl to some degree.

mail() will handle anything though. from  mail you could do anything you want. have a separate page for captcha  thaT ASKS  for the original email ... look I've drunk 1.5 l;itres of vodka sorry. I understand the problem but I can't explain it. PM me. anything for forum staff.

---

