---
title: "(urgent) Update my dynamic IP with zoneedit"
date: 2008-06-21
forum: Server Platforms
---

### Post by DeeBoo on 2008-06-21
Hello Guys,

I have worked more than 8 hours so far to find a solution to how to update my dynamic IP with zoneedit I am still beginner with ubuntu8.04.

I visited many sites in how to update your account in zoneedit each time your IP change but I could not.

Can anyone please tell me the procedure to do so ? 

each time my IP change I use these two codes : 

 lynx -source -auth=username: password 'http://dynamic.zoneedit.com/auth/dynamic.html?host=www.mydomain.com,mydomain.com'

wget -O - --http-user=username --http-passwd=password 'http://dynamic.zoneedit.com/auth/dynamic.html?host=www.mydomain.com,mydomain.com'

and I update my account manually but it is not a good solution to update manually I saw some solution about cron job but I could not make it .

please help me guys

---

### Post by hyper_ch on 2008-06-21
well, no-ip.com and dyndns.org habe both a client for ubuntu that just works... you maybe want to change the dyn service.

---

### Post by DeeBoo on 2008-06-21
I subscribe with ZoneEdit and I have a domain name for my server

---

### Post by mbeach on 2008-06-21
[EDIT: SEE NEXT POST ]

Those two lines work for you when you run them manually?

Who is your domain registered through?  If they allow you to create a CNAME record, it may a simpler task to use ddclient, and sign up with dyndns (free).  The CNAME record will then point to your dyndns url, which in turn points to your ip updated with ddclient.

Your other option is to create a script with your two lines, and run it on some regular interval using cron, or I suspect a better option is to only update when necessary (not sure exactly how ddclient handles that, but I'm sure its not a secret).  Not sure how zoneedit is with updating unnecessarily, but if they do have a policy about it, you'd want to have two files on your machine, your "oldip" and "newip" updating "newip" each time you check your current IP address.  If old and new are the same, do nothing, otherwise, set oldip equal to newip and run your update.  This way you'd be updating only when it was warranted.  

mb.

---

### Post by mbeach on 2008-06-21
According to:
[http://www.zoneedit.com/doc/dynamic.html#faq3](http://www.zoneedit.com/doc/dynamic.html#faq3)

ddclient is supported by zoneedit.

install using Synaptic or other favorite method then edit
/etc/ddclient/ddclient.conf
as necessary.

---

