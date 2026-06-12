---
title: "Problem with sendmail and send_form_email.php"
date: 2011-01-16
forum: Server Platforms
---

### Post by Spacerman on 2011-01-16
Hey. 
I have a problem getting a send_form_email.php to work... 
I think it has something to do with sendmail. 
Should I use postfix? or sendmail?

Can anyone help?

Here is the php:

<?php
if(isset($_POST['email'])) {
     
    // EDIT THE 2 LINES BELOW AS REQUIRED
    $email_to = "rods.lakkservice@gmail.com";
    $email_subject = "Subjekt";
     
     
    function died($error) {
        // your error code can go here
        echo "We are very sorry, but there were error(s) found with the form you submitted. ";
        echo "These errors appear below.<br /><br />";
        echo $error."<br /><br />";
        echo "Please go back and fix these errors.<br /><br />";
        die();
    }
     
    // validation expected data exists
    if(!isset($_POST['first_name']) ||
        !isset($_POST['last_name']) ||
        !isset($_POST['email']) ||
        !isset($_POST['telephone']) ||
        !isset($_POST['comments'])) {
        died('We are sorry, but there appears to be a problem with the form you submitted.');      
    }
     
    $first_name = $_POST['first_name']; // required
    $last_name = $_POST['last_name']; // required
    $email_from = $_POST['email']; // required
    $telephone = $_POST['telephone']; // not required
    $comments = $_POST['comments']; // required
     
    $error_message = "";
    $email_exp = "^[A-Z0-9._%-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$";
  if(!eregi($email_exp,$email_from)) {
    $error_message .= 'The Email Address you entered does not appear to be valid.<br />';
  }
    $string_exp = "^[a-z .'-]+$";
  if(!eregi($string_exp,$first_name)) {
    $error_message .= 'The First Name you entered does not appear to be valid.<br />';
  }
  if(!eregi($string_exp,$last_name)) {
    $error_message .= 'The Last Name you entered does not appear to be valid.<br />';
  }
  if(strlen($comments) < 2) {
    $error_message .= 'The Comments you entered do not appear to be valid.<br />';
  }
  if(strlen($error_message) > 0) {
    died($error_message);
  }
    $email_message = "Form details below.\n\n";
     
    function clean_string($string) {
      $bad = array("content-type","bcc:","to:","cc:","href");
      return str_replace($bad,"",$string);
    }
     
    $email_message .= "First Name: ".clean_string($first_name)."\n";
    $email_message .= "Last Name: ".clean_string($last_name)."\n";
    $email_message .= "Email: ".clean_string($email_from)."\n";
    $email_message .= "Telephone: ".clean_string($telephone)."\n";
    $email_message .= "Comments: ".clean_string($comments)."\n";
        
// create email headers
$headers = 'From: '.$email_from."\r\n".
'Reply-To: '.$email_from."\r\n" .
'X-Mailer: PHP/' . phpversion();
@mail($email_to, $email_subject, $email_message, $headers); 
?> 
<!-- include your own success html here -->
<?php
include("header.htm");
?>
<br><br><br><br><br>
<p align="center"> 
Takk for at du kontaktet oss. Vi skal svare så snart vi har anledning.
<br><br><br><br><br>
</p> 

<?php
include("footer.htm");
?>

<?
}
?>


And html:

<form name="contactform" method="post" action="send_form_email.php">
<table width="450px">
</tr>
<tr>
 <td valign="top">
  <label for="first_name">Fornavn *</label>
 </td>
 <td valign="top">
  <input  type="text" name="first_name" maxlength="50" size="30">
 </td>
</tr>
 
<tr>
 <td valign="top"">
  <label for="last_name">Etternavn *</label>
 </td>
 <td valign="top">
  <input  type="text" name="last_name" maxlength="50" size="30">
 </td>
</tr>
<tr>
 <td valign="top">
  <label for="email">E-post adresse *</label>
 </td>
 <td valign="top">
  <input  type="text" name="email" maxlength="80" size="30">
 </td>
 
</tr>
<tr>
 <td valign="top">
  <label for="telephone">Telefonnummer</label>
 </td>
 <td valign="top">
  <input  type="text" name="telephone" maxlength="30" size="30">
 </td>
</tr>
<tr>
 <td valign="top">
  <label for="comments">Spørsmål *</label>
 </td>
 <td valign="top">
  <textarea  name="comments" maxlength="1000" cols="34" rows="6"></textarea>
 </td>
 
</tr>
<tr>
 <td colspan="2" style="text-align:center">
  <input type="submit" value="Send">   
 </td>
</tr>
</table>
</form>

<br/><br/><br/>
</td>
</tr>
</table>


Mail.log:

Jan 16 15:27:29 (none) sm-mta[4715]: starting daemon (8.14.3): SMTP+queueing@00:10:00

Jan 16 15:39:01 (none) sendmail[4796]: p0GEd1v9004796: from=root, size=3511, class=0, nrcpts=1, msgid=<201101161439.p0GEd1v9004796@localhost.localdomain>, relay=root@localhost

Jan 16 15:39:01 (none) sm-mta[4797]: p0GEd1VF004797: from=<root@localhost.localdomain>, size=3799, class=0, nrcpts=1, msgid=<201101161439.p0GEd1v9004796@localhost.localdomain>, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127$

Jan 16 15:39:01 (none) sendmail[4796]: p0GEd1v9004796: to=root, ctladdr=root (0/0), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=33511, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p0GEd1VF004797 Message accepted for delive$

Jan 16 15:39:01 (none) sm-mta[4798]: p0GEd1VF004797: to=rods.lakkservice@gmail.com, ctladdr=<root@localhost.localdomain> (0/0), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=34049, relay=smtp.lyse.net. [81.167.36.150], dsn=2.0.0, st$


My problem is that when I push the send button I don't get the email.

Any help would be appreciated.

---

### Post by SeijiSensei on 2011-01-16
My guess is that your relay host, smtp.lyse.net, probably won't forward a message from "root@localhost.localdomain".  You need a sender with a legitimate address.  It looks like the script uses "$email_from" as the sender address, but the log doesn't agree.  I noticed that the $headers string uses "\n\r" to denote a new line.  This is a Window/DOS feature.  Try replacing "\n\r" with just "\n".

Also, in sendmail, the user under which the Apache server runs needs to be added to /etc/mail/trusted-users so it can change the SMTP envelope sender.  I'm guessing this is the root of your problem.  On Ubuntu, that user is called "www-data", so add "www-data" to the trusted-users file.

BTW, forms that let the user specify both the From and To addresses lend themselves to abuse by spammers.  I only use forms that send the message to a specified address that's hidden in the script.

---

### Post by Spacerman on 2011-01-16
Ok.   
Thank you for your help. I'll see what I can do about that. I thought the form I used was supposed to send only to the address i specified in the php file...

---

### Post by SeijiSensei on 2011-01-16
> **Spacerman said:**
> Ok.   
Thank you for your help. I'll see what I can do about that. I thought the form I used was supposed to send only to the address i specified in the php file...

Ah, you're right.  The $email_to address is fixed within the script.  Sorry I missed that.

---

