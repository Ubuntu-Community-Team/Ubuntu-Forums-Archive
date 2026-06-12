---
title: "Is this as bad as I think it is?"
date: 2010-10-15
forum: Security
---

### Post by an0dos on 2010-10-15
Yesterday I was given the responsibility at work to upload some files to an offsite 3rd party FTP server. Apparently we use a "secure" proprietary web-based java FTP client.

The FTP client was buggy and repeatedly crashed. While I was waiting for it to work, I decided to look at the HTML of the website when I was logged in to their FTP server. It contained the following lines:

```

hostname="-------------" \
			username="--------" \
			password="--------" \
			connectionType="ftps" \
			mode="binary" \
			enableHost="false" \
			enableConnectionType="false" \
			enableAnonymous="false" \

```

I substituted dashes for the sensitive information that was in the website. I do not have access to analyze the network traffic to see if our username and password is being transmitted in plain text to the website. It makes me nervous to see the username and password plainly written out in the html for a website; however analyzing the network traffic and securing networks is not part of my job description. So my question for people here who have this as part of their job description is as follows:

Is this a bad thing? Am I overreacting? Should I talk to our IT guy about FileZilla?

---

### Post by CharlesA on 2010-10-15
Wow. Was it at least using HTTPS?

I'd defintiely tell the IT guys to check out filezilla for transfering over secure ftp.

Were the credentials there when you weren't logged in?

---

### Post by an0dos on 2010-10-15
> **CharlesA said:**
> Wow. Was it at least using HTTPS?

I'd defintiely tell the IT guys to check out filezilla for transfering over secure ftp.

Were the credentials there when you weren't logged in?

It was not HTTPS. 
I was able to view the credentials in a cached version of the page. I also believe the credentials were stored in the form of a session cookie.


The HTML for the login page 
> 
    <p><span class="header"><center>Web Based Java FTP Client</center></span></p> 
      <p align="center"> 
<FORM NAME="login" ACTION="login.cfm" METHOD="POST" onSubmit="return _CF_checklogin(this)" ENCTYPE="multipart/form-data"> 
 
 
  <table width="319" align="center"> 
    <tr> 
      <td align="right" width="96"><b>Username:</b></td> 
      <td align="left" width="209"> 
        <p align="left"><input maxLength="256" name="ftpuser" size="20"></p> 
      </td> 
    </tr> 
    <tr> 
      <td align="right" width="96"><b>Password:</b></td> 
      <td align="left" width="209"> 
        <p align="left"><input type="password" maxLength="256" value name="ftppass" size="20"></p> 
      </td> 
    </tr> 
	<tr> 
      <td align="right" width="96"><b>Method:</b></td> 
      <td align="left" width="209"> 
        <p align="left"><select size="1" name="method"> 
  								<option value="Normal">Normal FTP</option> 
  								<option value="Secure" selected>Secure FTP</option> 
							</select></p> 
      </td> 
    </tr> 
    <tr> 
      <td align="middle" colSpan="2" width="311"> 
        <p align="center"><input type="submit" value="Log into Java FTP Client"></p> 
      </td> 
    </tr> 
  </table> 
 
</FORM> 


I do not have permission to access the server from home.

---

### Post by CharlesA on 2010-10-15
That doesn't sound good for security at all.

I guess the only thing you can really do is bring it to the attention of the IT guys and let them decide what to do.

---

### Post by an0dos on 2010-10-15
> **CharlesA said:**
> That doesn't sound good for security at all.

I guess the only thing you can really do is bring it to the attention of the IT guys and let them decide what to do.

Yep. I guess so. Time to put on the tin foil hat.

---

### Post by pricetech on 2010-10-15
Definitely bring it to the attention of IT, and perhaps management.  If the stuff you are transferring has any value at all, it needs to be secured.

---

### Post by BkkBonanza on 2010-10-15
There doesn't appear to be any Java applet in that page either that could have possibly encrypted data during xfer. I don't see an applet tag or any indication that the file isn't using regular multipart/form-data. 

Also you would want to inspect the javascript _CF_checklogin function to see what it does. It could use an https asynchronous call in the background to provide security but from what we see here there's no way to know.

---

### Post by Cool Javelin on 2010-11-19
Well, I am going to play the roll of an alarmist and tell you the sky is falling, please disregard if I am way off base.

I don't know anything about your organization or your position in it, (how big it is, how secure your job is, what the data is all about, etc...) and I don't want to know.

Having said that, you might think about the acronym CYA or COVER YOUR *** !!!

Send your concerns to management via email and keep copies yourself so later if something happens and bad guys get into their data, you can say "I told you so". Not so much to your boss, but to any authorities that com-a-knockin.

Take care how you keep copies too. If it is a secure company you might get in trouble if you remove USB sticks, and stuff.

Definitely don't cc or bcc copies to your own personal email.

Old school printing and mail may work, or get a fax machine at home and fax from work (not directly from your computer, print it first, then shred the original.)

My wife worked for a .com company that was getting into some shady stuff. She was in constant communication with management about some doings and was uncomfortable for a long time. She kept copies of her emails and later in the bankrupcy (and other) courts, they tried to pin some of the bad stuff on her saying they had no idea what was happening, yadda, yaddy yadda....

She had emails to prove she was not only given explicit instructions but also to keep it secret. The owners went to jail and she walked away (without a job of course, but she could have gone to jail and lost her job.)

Depending on your place in life, this company and what you are doing, you may be in a bad spot. These things have a habit of blowing up on you.

Good luck.

Just my 23 cents (inflation.)

Mark.

---

