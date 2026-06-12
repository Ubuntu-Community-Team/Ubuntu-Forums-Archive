---
title: "Sendmail problems"
date: 2011-09-23
forum: Server Platforms
---

### Post by celtic_smith on 2011-09-23
Hi everybody, 

I have a webserver on my home network to serve my personal website.  I  have been trying to teach myself all of this and the website is working  well except that my contact form will not send out any email.  I'm not  trying to host my own mailserver, all I want is for the contact form to  send out mail to my gmail address.  it is my understanding that all I  need for this is the default sendmail client, and should not have to  bother with postfix, or anything more complicated yet.

I know that sendmail is working as I can use it to send mail from the server using the command line.  

The php mail() function returns that the mail has been sent ok, it just never gets to the intended recipient.

I have edited the php.ini file so that it points to the sendmail directory 

I have a static ip address though my internet provider, and the rest of the website is working just great.

I am posting what I think is all of the pertinent code and log files  below, please do not hesitate to let me know if there is anything else  that is needed.

```
sendmail mygmail@gmail.com
         This is a test

```sends an email just fine and shows as having been sent from [EMAIL="myusername@servername.domain.ca"]myusername@servername.domain.ca[/EMAIL]

and produces this entry in the mail log

```
ep 23 12:59:48 servername sendmail[23360]: p8NFxNCG023360:  from=username, size=41, class=0, nrcpts=1,  msgid=<201109231559.p8NFxNCG023360@servername.domainname.ca>,  relay=username@localhost
Sep 23 12:59:48 servername sm-mta[23362]: p8NFxmbv023362:  from=<username@servername.domainname.ca>, size=360, class=0,  nrcpts=1,  msgid=<201109231559.p8NFxNCG023360@servername.domainname.ca>,  proto=ESMTP, daemon=M$
Sep 23 12:59:48servername sendmail[23360]: p8NFxNCG023360: to=mygmail  address@gmail.com, ctladdr=username (1000/1000), delay=00:00:25,  xdelay=00:00:00, mailer=relay, pri=30041, relay=[127.0.0.1] [127.0.0.1],  dsn=$
Sep 23 12:59:49 servername sm-mta[23364]: STARTTLS=client,  relay=gmail-smtp-in.l.google.com., version=TLSv1/SSLv3, verify=FAIL,  cipher=RC4-SHA, bits=128/128
Sep 23 12:59:50 servername sm-mta[23364]: p8NFxmbv023362:  to=<mygmail@gmail.com>,  ctladdr=<username@servername.domainname.ca> (1000/1000),  delay=00:00:02, xdelay=00:00:02, mailer=esmtp, pri=120360,  relay=gm$
```however if I press send on the contact form using this php layout

[PHP]                <div id="contact-area">
                         <script type="text/javascript">
 var RecaptchaOptions = {
    theme : 'white'
 };
 </script>
                        <form method="post" action="contactengine.php">
                                <label for="Name">Name:</label>
                                <input type="text" name="Name" id="Name" />

                                <label for="Subject">Subject:</label>
                                <input type="text" name="Subject" id="Subject" />

                                <label for="Email">Email:</label>
                                <input type="text" name="Email" id="Email" />

                                <label for="Message">Message:</label><br />
                                <textarea name="Message" rows="20" cols="20" id="Message"></textarea>
                                
                                <div id="captcha-area">

                                <?php
  require_once('recaptchalib.php');
                                $publickey = "public recaptcha key";
                                $privatekey = "private recaptcha key";

                                # the response from reCAPTCHA
                                $resp = null;
                                # the error code from reCAPTCHA, if any
                                $error = null;

                                # are we submitting the page?
                                if ($_POST["submit"]) {
                                  $resp = recaptcha_check_answer ($privatekey,
                                                                                                  $_SERVER["REMOTE_ADDR"],
                                                                                                   $_POST["recaptcha_challenge_field"],
                                                                                                   $_POST["recaptcha_response_field"]);
                                
                                  if ($resp->is_valid) {
                                        echo "You got it!";
                                        # in a real application, you should send an email, create an account, etc
                                  } else {
                                        # set the error code so that we can display it. You could also use
                                        # die ("reCAPTCHA failed"), but using the error message is
                                        # more user friendly
                                        $error = $resp->error;
                                  }
                                }
                                echo recaptcha_get_html($publickey, $error);
                                ?>
                                
                                </div>

                                <input type="submit" name="submit" value="Submit" class="submit-button" />
                        </form>
[/PHP]which uses the contact engine written as follows

[PHP]<?php
        require_once('recaptchalib.php');
        $privatekey = "Private Recaptcha keyI";
        $resp = recaptcha_check_answer ($privatekey,
        $_SERVER["REMOTE_ADDR"],
        $_POST["recaptcha_challenge_field"],
        $_POST["recaptcha_response_field"]);
        if (!$resp->is_valid) {
        die ("The reCAPTCHA wasn't entered correctly. Go back and try it again." .
        "(reCAPTCHA said: " . $resp->error . ")");
        }


$EmailFrom = "Website Contact Form,";
$EmailTo = "mygmailaddress@gmail.com";
$Name = Trim(stripslashes($_POST['Name'])); 
$Subject = Trim(stripslashes($_POST['Subject'])); 
$Email = Trim(stripslashes($_POST['Email'])); 
$Message = Trim(stripslashes($_POST['Message'])); 

// validation
$validationOK=true;
if (!$validationOK) {
  print "<meta http-equiv=\"refresh\" content=\"0;URL=error.htm\">";
  exit;
}

// prepare email body text
$Body = "";
$Body .= "Name: ";
$Body .= $Name;
$Body .= "\n";
$Body .= "Subject: ";
$Body .= $Subject;
$Body .= "\n";
$Body .= "Email: ";
$Body .= $Email;
$Body .= "\n";
$Body .= "Message: ";
$Body .= $Message;
$Body .= "\n";

// send email 
$success = mail($Name, $Subject, $Body, "From: <$EmailFrom>");

// redirect to success page 
if ($success){
  print "<meta http-equiv=\"refresh\" content=\"0;URL=thankyou.php\">";
}
else{
  print "<meta http-equiv=\"refresh\" content=\"0;URL=error.htm\">";
}
?>

[/PHP]and produces the following in my mail log

```
Sep  23 15:09:02 servername sendmail[23581]: p8NI92xg023581: from=www-data,  size=209, class=0, nrcpts=1,  msgid=<201109231809.p8NI92xg023581@servername.domainname.ca>,  relay=www-data@localhost
Sep 23 15:09:02 servername sm-mta[23582]:  p8NI92sK023582: < (the name I entered in the name field inthe contact  form) bob.mctesterson@servername.domainname.ca>... User unknown
Sep  23 15:09:02 servername sendmail[23581]: p8NI92xg023581: to=Bob  McTesterson(name I used in the name field of the contact form),  ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay,  pri=30209, relay=[127.0.0.1] [127.0.0.1], dsn=5.1.1, st$
Sep 23  15:09:02 servername sm-mta[23582]: p8NI92sK023582:  from=<www-data@hyperion.serenebirth.ca>, size=209, class=0,  nrcpts=0, proto=ESMTP, daemon=MTA, relay=localhost.localdomain  [127.0.0.1]
Sep 23 15:09:02 servername sendmail[23581]: p8NI92xg023581: p8NI92xh023581: DSN: User unknown
Sep  23 15:09:02 servername sm-mta[23582]: p8NI92sM023582: from=<>,  size=2272, class=0, nrcpts=1,  msgid=<201109231809.p8NI92xh023581@servername.domainname.ca>,  proto=ESMTP, daemon=MTA, relay=localhost.localdoma$
Sep 23 15:09:02  servername sendmail[23581]: p8NI92xh023581: to=www-data, delay=00:00:00,  xdelay=00:00:00, mailer=relay, pri=31233, relay=[127.0.0.1]  [127.0.0.1], dsn=2.0.0, stat=Sent (p8NI92sM023582 Message a$
Sep 23  15:09:03 servername sm-mta[23583]: p8NI92sM023582:  to=<www-data@srevername.domainname.ca>, delay=00:00:01,  xdelay=00:00:00, mailer=local, pri=32516, dsn=2.0.0, stat=Sent

```I know that something is not right but have exhaiseted my google-fu.  Can anyone give me an idea of where i've gone wrong?  Most of that I have read seems to suggest that what I'm doing here should work right out of the box.

---

### Post by Ryan Dwyer on 2011-09-24
For a start, you're trying to send an email to the user's name and not your email address. The first parameter for mail() should be $EmailTo.

Next, the From header should be an email address or a name + email address. You have a name only. This may or may not work. Set it to "From: Website Contact Form <mygmailaddress@gmail.com>".

Then test again and if you still don't have it, check that it didn't go into spam.

---

### Post by SeijiSensei on 2011-09-26
Only "trusted users" can set the SMTP "envelope" From address, the address that the remote SMTP server sees.  That address need not match the From address that appears in the message headers.  The envelope From appears at the top of each message in the Return-Path header.

If you send a message via PHP, the envelope from will be [email]www-data@host.domain[/email] because the www-data user owns the Apache process that's sending the mail.  

Look at sendmail.cf and find the line that begins Ft.  It should be followed with the name of the file that contains trusted users like Ft/etc/mail/trusted-users.  Add www-data to that file if it's not already there, and restart sendmail.

---

### Post by collisionystm on 2011-09-26
Do you have a registered domain? You can only send from a domain that is legally registered. Spend 10 bucks a year at godaddy.com to do it.

---

