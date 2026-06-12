---
title: "cart apllication for e-com site"
date: 2011-08-03
forum: Server Platforms
---

### Post by fdrake on 2011-08-03
Has anyone ever worked in the development of a cart application able to handle transactions and payment. I am not just interested in the database processing but how the money is being transfered. Do you need some server requirements? Any book(s) that you find useful to read? or online source ?

---

### Post by Lars Noodén on 2011-08-03
The money transfer depends on which service(s) you are using to get the payment.   Basically, you can farm this out to the payment service and get back a Yes/No response in regards to payment.

For example, Moneybookers has a good description of their [simple API](http://www.moneybookers.com/app/help.pl?s=m_shoppingcart) and a more [in-depth details on payment](http://www.moneybookers.com/merchant/en/automated_payments_interface_manual.pdf).

Edit: That example also allows set up of a test account to get the APIs working without testing on real money.

---

### Post by fdrake on 2011-08-03
thanks Lars Noodén for your reply, Moneybookers is exactly what I was looking for. I will give it a shot.

---

