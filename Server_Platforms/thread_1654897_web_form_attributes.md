---
title: "web form attributes"
date: 2010-12-29
forum: Server Platforms
---

### Post by entertheraptor on 2010-12-29
Hi all, I'm running Ubuntu 10.10 server which was installed as per the Perfect Server - Ubuntu 10.10 [ISPConfig 3] guide on HowtoForge.com.
[http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3)

So I'm running Postfix mail server along with both SquirrelMail and Roundcube as webmail clients.

What I want to do is place a webform on a page in one of my sites and need to know what to put in the "method" and "action" attributes in the "form" tag to get it to send to a email addy and how to configure the server to achieve this too.

As you can probably tell except for being able to copy and paste code and navigate the server from the command line I have little idea what I'm doing so feel free to treat this as a "Dummies Guide To".

Thanks in advance.

---

### Post by Calimo on 2010-12-29
Hi,

"method" can be one of "[GET]("http://en.wikipedia.org/wiki/GET_%28HTTP%29#Request_methods")" or "[POST]("http://en.wikipedia.org/wiki/POST_%28HTTP%29")". As you're triggering an action on the server side (sending an email), I'd recommend POST.
Keep "GET" for when you just fetch data and display it without having any side-effect on the server.

The "action" must be the URL to a script that will be processing the form data and send the email. Typically it will be a perl or php script. You cannot call postfix directly. Type something as "php contact form" in your favorite search engine to get hundreds of examples. [This one with jQuery validation]("http://www.raymondselda.com/php-contact-form-with-jquery-validation/") looks pretty nice (and I think security is adequate), but I haven't tested.

---

### Post by koenn on 2010-12-29
quick, easy, simple :

make a form like this one
```

<form action="mailto:admin@example.com" enctype="text/plain" method="post">

   <p>Name: <input name="Name" type="text" id="Name" size="40"></p> 

    <p>Comment:</p>
    <p><textarea name="Comment" cols="55" rows="5"
      id="Comment"></textarea></p>

    <p><input type="submit" name="Submit" value="Submit"></p>
</form>

```


on subit, the mailto; URL  in the action attrubute of the form tag is triggered and a message gets sent, containing the input field names and their values. 
It depends on the _browser_'s capability to succesfully process a mailto: url and invoke a mail program; you may want to test this.

---

### Post by entertheraptor on 2010-12-29
thanks for the reply Koenn but I'm trying to find out how to do this "server side".

The issues with your method are 1, it relies on the client using their email client. I know lots of people who use webmail exclusively. and 2, this method doesn't hide your email addy from bots and harvesters which is the primary reason for wanting to set up a form rather than just posting a mailto link to my addy on the page.

Thanks anyway :)

---

### Post by James78 on 2010-12-29
Small php program to email from a form. Not tested, but should work, let me know if there's any errors, and I'll fix it. Also, this DOES NOT stop bots from filling out the form and pressing submit to send you spam, but there's no way they can get your email address since it's server side. Anyways, just name it something like "emailus.php", style it or whatever, improve it, upload and throw a link to it on your site, and you're done.
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
     "http://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
<title>Contact me!</title>
</head>
<body>
Send me an email<br><br>
<form method="post" action='./'>
Source Email: <input type="text" name="sourceemail"><br><br>
Subject: <input type="text" name="subject"><br><br>
Message Body:<br>
<textarea name="message" cols="40" rows="5">Default message here...</textarea><br><br>
<input type="submit" name="send" value="Go">
</form>
<?php
//If go button is pressed...
if(isset($_POST['send'])) {
    $sourceemail = $_POST['sourceemail'];
    $destinationemail = 'your-destination-email-here@domain.com'
    $message = $_POST['message'];
    $subject = $_POST['subject'];

    if(($sourceemail && $message && $subject) != '') {
        mail($destinationemail, $subject, $message, $sourceemail);
        echo '<br><b>Email has been sent.</b>';
    }
    else {
        echo '<br><font color="#ff0000"><b>FILL OUT ALL THE FIELDS</b></font>';
    }
}
?>
</body>
</html>
```

Now, personally, what did I do? I used a mailto, BUT, with one defining difference. It's soo secret, I can't mention it in public, I sent you a PM, only share with trusted people, can't have this getting out, that's when bots start being made to recognize it.

---

### Post by entertheraptor on 2010-12-31
> **Calimo said:**
> Hi,

"method" can be one of "[GET]("http://en.wikipedia.org/wiki/GET_%28HTTP%29#Request_methods")" or "[POST]("http://en.wikipedia.org/wiki/POST_%28HTTP%29")". As you're triggering an action on the server side (sending an email), I'd recommend POST.
Keep "GET" for when you just fetch data and display it without having any side-effect on the server.

The "action" must be the URL to a script that will be processing the form data and send the email. Typically it will be a perl or php script. You cannot call postfix directly. Type something as "php contact form" in your favorite search engine to get hundreds of examples. [This one with jQuery validation]("http://www.raymondselda.com/php-contact-form-with-jquery-validation/") looks pretty nice (and I think security is adequate), but I haven't tested.

I used the script you linked to and it works great. Thanks heaps.

---

### Post by koenn on 2011-01-01
> **entertheraptor said:**
> thanks for the reply Koenn but I'm trying to find out how to do this "server side".

The issues with your method are 1, it relies on the client using their email client. I know lots of people who use webmail exclusively. and 2, this method doesn't hide your email addy from bots and harvesters which is the primary reason for wanting to set up a form rather than just posting a mailto link to my addy on the page.

Thanks anyway :)
yeah, I know, it's simple but hassome downsides, and I wasn't sure myself how well it would work with web mail. 
I think the address in the mailto: could be obfuscated, though. 
I don't do web design myself, so I only use this for proof of concepts and prototypes on intranets, where you know what the client side looks like (email clients etc)

---

### Post by James78 on 2011-01-02
> **koenn said:**
> yeah, I know, it's simple but hassome downsides, and I wasn't sure myself how well it would work with web mail. 
**I think the address in the mailto: could be obfuscated, though.** 
I don't do web design myself, so I only use this for proof of concepts and prototypes on intranets, where you know what the client side looks like (email clients etc)
That's how my alternate method worked. ;)

---

### Post by Calimo on 2011-01-02
> **entertheraptor said:**
> thanks for the reply Koenn but I'm trying to find out how to do this "server side".

The issues with your method are 1, it relies on the client using their email client. I know lots of people who use webmail exclusively. and 2, this method doesn't hide your email addy from bots and harvesters which is the primary reason for wanting to set up a form rather than just posting a mailto link to my addy on the page.

Thanks anyway :)You can use an alias instead of your true address. There are tons of free redirection services, and if you control your mail server you can create your own aliases. Then when it gets spammed, drop it and pick a new one. Unless you have a huge site, you won't be doing it that often.

> **James78 said:**
> Now, personally, what did I do? I used a mailto, BUT, with one defining difference. It's soo secret, I can't mention it in public, I sent you a PM, only share with trusted people, can't have this getting out, that's when bots start being made to recognize it.
Don't trust [security through obscurity](http://en.wikipedia.org/wiki/Security_through_obscurity). If your secret ever comes out, you'll be in serious trouble! You should prefer truly robust and secure solutions, so if anything turns bad all isn't lost!

---

### Post by Calimo on 2011-01-02
Just one more thing. As James78 mentioned you will be getting spam through the form. There are simple workaround, though.

First and simplest one: spammers will provide a fake address, with an non-existent domain (such as quhdgb.com). I had several of them, but you can filter them easily.
I have a form in Perl and used the Net::DNS module to find out if the domain has an MX entry. If it hasn't you'll never be able to send the answer, so just discard it if you like (you may reject non spammer clients who doesn't want any answer and provide a false email address)

If it isn't sufficient (for me it was: small personal website, didn't got a spam for months), you can have a look at tools like Akismet to detect spams submissions. Again you'll have false positive, so keep a log and review it when you have some time.

---

