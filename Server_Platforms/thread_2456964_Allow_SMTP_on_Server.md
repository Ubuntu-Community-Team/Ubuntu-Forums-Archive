---
title: "Allow SMTP on Server"
date: 2021-01-22
forum: Server Platforms
---

### Post by pauldechampignon on 2021-01-22
I have recently purchased VPS with Ubuntu installed to deploy my page - ASP.NET Core 3.1 API/Services along with Angular Front End.

I have problem with my API Services though. One part of it is simple code responsible for sending an email typed in front end form. Everything works great locally but once deployed I got an error:

> 
The server committed a protocol violation. The server response was: UGFzc3dvcmQ6
   at System.Net.Mail.MailCommand.CheckResponse(SmtpStatusCode statusCode, String response)
   at System.Net.Mail.MailCommand.Send(SmtpConnection conn, Byte[] command, MailAddress from, Boolean allowUnicode)
   at System.Net.Mail.SmtpTransport.SendMail(MailAddress sender, MailAddressCollection recipients, String deliveryNotify, Boolean allowUnicode, SmtpFailedRecipientException& exception)
   at System.Net.Mail.SmtpClient.Send(MailMessage message)
   at API.Controllers.SampleController.SendEmail(PostObject postObject) in /home/ubuntu/SampleCoreAPI/API/Controllers/SampleController.cs:line 166


Checking this error it looks there's something wrong with authorization of my request. I have even written to hosting support asking about possible blockades they might impose on users in order to avoid sending spam but they confirmed they do not use such things unless the traffic containing emails is significant. They mentioned I should "open SMTP ports". How shjould I understand this? I tried "sudo ufw allow 25" and "sudo ufw allow 587" but it has not helped at all and I get the same error - UGFzc3dvcmQ6.

I also tried deploying my API on Azure and it works all fine there so I assume it's something with allowing SMTP traffic on my VPS.

Before receiving this error I had an error related to GSSAPI and I installed gss-ntlmssp which is:

> 
[COLOR=#333333][FONT=&amp]*GSSAPI NTLMSSP Mechanism -- MIT GSSAPI plugin*[/FONT][/COLOR]
*GSS-NTLMSSP is a GSSAPI mechanism plugin that implements NTLMSSP. NTLMSSP is a Microsoft Security Provider that implements various versions and falvors of the NTLM challenge-response family. . GSS-NTLMSSP, implements both NTLM and NTLMv2 and all the various security variants to the key exchange that Microsoft introduced and documented over time. . This code implements the NTLMSSP mechanism as a GSSAPI loadable mechanism and has been tested to work with MIT Kerberos' 1.11 implementation of GSSAPI. . This package supplies the MIT GSSAPI plugin.*

Perhaps someone encountered issue like this during deployment process?

---

### Post by SeijiSensei on 2021-01-22
You're apparently having problems with outbound mail. Opening the SMTP ports should do nothing for that unless you're blocking ports on localhost (127.0.0.1). 

Here's a quick test.  If you can get a shell on your VPS, first determine the identity of the MX host for the domain to which you are sending.

```
host -t mx domain.name
``` 

Here's an example of the output for gmail.com:
```

$ host -t mx gmail.com
gmail.com mail is handled by 5 gmail-smtp-in.l.google.com.
gmail.com mail is handled by 40 alt4.gmail-smtp-in.l.google.com.
gmail.com mail is handled by 10 alt1.gmail-smtp-in.l.google.com.
gmail.com mail is handled by 30 alt3.gmail-smtp-in.l.google.com.
gmail.com mail is handled by 20 alt2.gmail-smtp-in.l.google.com.

```

Next, choose the host with the lowest "priority" as represented by the number before each host's name.  The primary MX for gmail is gmail-smtp-in.l.google.com as indicated by its priority of 5.  Now run the command:
```
telnet gmail-smtp-in.l.google.com 25
```
using the hostname for your email account instead of gmail-smtp-in.l.google.com.  You should get a reply from the server like this:
```
telnet gmail-smtp-in.l.google.com 25
Trying 173.194.208.27...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP x186si5178934qke.302 - gsmtp

```
What do you see?

---

### Post by pauldechampignon on 2021-01-22
Hey, thank you for quick answer!

So, with telnet - I was already testing it and I am able te send email to myself.

My mail server is: pro2.mail.ovh.net

When I try typing 

```
[COLOR=#000000][FONT=&amp]host -t mx [/FONT][/COLOR]pro2.mail.ovh.net
```

I get:

```

pro2.mail.ovh.net has no MX record

```

If I test it for mail.ovh.net or ovh.net I get:

```

mail.ovh.net mail is handled by 5 mx1.mail.ovh.net.
mail.ovh.net mail is handled by 50 mx2.mail.ovh.net.
mail.ovh.net mail is handled by 1 mx0.mail.ovh.net.
mail.ovh.net mail is handled by 100 mx3.mail.ovh.net.

```

and 

```

ovh.net mail is handled by 5 mx2.ovh.net.
ovh.net mail is handled by 1 mx1.ovh.net.


```

respectively. 

When using telnet command I receive:

```
ubuntu@vps-30217c0c:~$ telnet mx0.mail.ovh.net 25Trying 178.33.252.245...
Connected to mx0.mail.ovh.net.
Escape character is '^]'.
220-mx0.mail.ovh.net in34
220 mx0.mail.ovh.net in34

```
for mail.ovh.net

or 

```

ubuntu@vps-30217c0c:~$ telnet mx1.ovh.net 25
Trying 188.165.47.122...
Connected to mx1.ovh.net.
Escape character is '^]'.
220-mx1.ovh.net in36
220 mx1.ovh.net in36

```

for ovh.net.

If I check telnet query against pro2.mail.ovh.net I get:

```

ubuntu@vps-30217c0c:~$ telnet pro2.mail.ovh.net 25
Trying 37.59.145.2...
Connected to pro2.mail.ovh.net.
Escape character is '^]'.
220 pro2.mail.ovh.net Microsoft ESMTP MAIL Service ready at Sat, 23 Jan 2021 01:19:42 +0100

```

---

### Post by CharlesA on 2021-01-23
I don't know if this helps, but googling "The server response was: UGFzc3dvcmQ6" returns that "UGFzc3dvcmQ6" is base64 encoded version of "Password:".

How is your application trying to send mail?

---

### Post by pauldechampignon on 2021-01-23
I googled this before and also tried base64 password encoind. Unfortunately it did not help.

If you ask about sending email it's just simple code:

```

        public async Task SendMessage(MessageQuery messageQuery)
        {
            var smtpClient = new SmtpClient("pro2.mail.ovh.net", 587);
            smtpClient.Credentials = new NetworkCredential(<<EMAIL ADDRESS>>, _configuration["MailboxSettings:Password"]);
            smtpClient.EnableSsl = false;


            var mailMessage = new MailMessage
            {
                Subject = $"New message from {messageQuery.Name} - {messageQuery.EmailAddress}",
                Body = messageQuery.MessageBody,
                From = new MailAddress(<<EMAIL ADDRESS>>)
            };


            mailMessage.To.Add(<<EMAIL ADDRESS>>);


            List<Task> tasks = new List<Task> {smtpClient.SendMailAsync(mailMessage)};


            await Task.WhenAll(tasks);
        }

```

I tried both enabling and disabling SSL. 

I have not yet installed SSL certificate on my VPS. Perhaps this might be causing this?

---

