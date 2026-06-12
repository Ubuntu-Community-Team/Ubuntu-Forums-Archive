---
title: "How secure is ubuntu for online banking"
date: 2008-05-18
forum: Security
---

### Post by BXA121 on 2008-05-18
Im quite reserved about using my banking information over the internet. Whenever i have ever needed to deal with my monies, ive always spoken to a person 1 on 1, i have never used telephone or the internet to bank. 

I know it can be unsafe and there is risk of my info being taken off me as it has been demonstrated by past "cock ups" heard from the news etc. 

how safe is online banking, does it matter if the OS is windows or ubuntu? Can my information still be exploited once it leaves my computer?

How does one make their system secure to do online banking?

Any ideas?

---

### Post by peitschie on 2008-05-18
A good question to ask.

The short answer is that the majority of the banking insecurities are actually the fault of the user visiting a site or installing a program they shouldn't.  Avoiding these, and your banking experiences will be secure.

Windows is a little more insecure by default, and has many more virus/trojan related problems that make it a little more dangerous to use.  Linux doesn't have many of these issues (yet...), and thus is safer.

Some good tips to keep in mind:
[LIST]
[*]Never respond to, or click on any links in an email pretending to be from your Bank (or Credit Card company, or paypal etc.).  Follow the next dot point to access your bank instead.
[*]ALWAYS visit your banking site by typing the address in the address bar (or perhaps using your own personally created shortcut).  This stops you from being taken to a "pretend" bank site as used in "Phishing" scams ([http://en.wikipedia.org/wiki/Phishing](http://en.wikipedia.org/wiki/Phishing))
[*]Don't install programs from untrusted sources.  Under linux this is still relevant.  The primary difference is that under Windows they often install themselves without your knowledge
[*]Never give out your PIN number or security details to anyone, either by phone or email
[/LIST]

If you run windows, keep a good firewall running, an up-to-date antivirus program, and a malware scanner of some sort AND are very careful about what demo programs or freeware programs you install (and what emails you even open), you will stay safe.

On linux, it tends to be a little easier.  Just don't install a program by someone you don't trust.  This means sometimes double-checking what others say about programs you might want to install.

It is very possible to have secure internet banking.  For all the people that get compromised, there are many more who have a perfectly safe experience with online banking.  Just don't forget those key rules you were taught as a kid: Never trust a stranger

(I do appreciate the irony in this statement in that it might convince you not to trust what I have written :lolflag:)

---

### Post by BXA121 on 2008-05-18
i do use pay pal and eBay, i buy stuff overseas with this stuff, so i understand where you are coming from with the phishing crap. 
do i need a firewall for my Ubuntu system if i want it secure?

regards

---

### Post by Lycaon on 2008-05-18
Peitschie made some good statements there! 
As for your question about using a firewall in ubuntu, well it's merely how paranoid you are BXA121. A firewall is always a good thing to have, you can have almost full control in outgoing/incomming data. (If some program tries to send some private information about your banking to a criminal). So yes it will increase your security. But is it nesceserry? That's up to you. 
I believe that most hacks concerning banking stuff are done by social hacking, like phished sites and fake mails etc. Our bank uses an sms system wich sends you a generated code. This code has to be entered in the banks website. Everytime you need to do something on the banks site, it will require a new code (accepting transactions etc). This cannot be spoofed easily by hacking/cracking your system. Other banks, as far as i know, have systems that are likewise secure. 

Main message: Use your brain when surfing, double check banking stuff, don't trust weird emails concerning banking stuff and don't install "weird" programms.

Generally online banking can be secure.

---

### Post by Dr Small on 2008-05-18
Don't use the banking website unless they encrypt the connecton (example, SSL, TLS). And also, verify their certificate.

---

### Post by aysiu on 2008-05-18
I disagree about typing the bank's URL manually in the address bar. If you mistype, you may end up at a phishing site by accident.

It's much better to use a search engine to find your bank's website, as the genuine bank site will probably be at the top of the search results (you can always verify this by looking at the URL).

---

### Post by drsox1899 on 2008-05-19
> **aysiu said:**
> I disagree about typing the bank's URL manually in the address bar. If you mistype, you may end up at a phishing site by accident.

It's much better to use a search engine to find your bank's website, as the genuine bank site will probably be at the top of the search results (you can always verify this by looking at the URL).

Don't agree.  Search engines are the best source of duff websites.  Only use a website that comes from a direct link from the bank.  i.e. by post or direct contact.

---

### Post by aysiu on 2008-05-19
> **drsox1899 said:**
> Don't agree.  Search engines are the best source of duff websites.  Only use a website that comes from a direct link from the bank.  i.e. by post or direct contact.
Huh? So you're supposed to click on a link in an email from a bank? No, I totally disagree. Links in email are *the* primary source of phishing scams.

If I'm looking for *Wachovia Bank* in Google, the first result is Wachovia's website. If I search for *Wachova Bank*, not only does Google list the actual Wachovia website as the first result, it also says > Did you mean: wachovia bank? If, however, I type *wachova.com* in the address bar, I get taken to a sketchy site.

Please, if you believe the search engines won't take you to a proper bank site, give me at least an example of this.

---

### Post by utUtu on 2008-05-19
I normally have separate box just for banking and paying my utilities, and not used for anything else.

If I were you I won't even use it for paypal or ebay.

Once you have established your banks/payee 's sites, bookmark them.  Take control of your cookies, and use Firefox without any add-ons/extensions.  Disable the xpinstall in about:config - I don't see reason why anyone else but me installing anything in my box.

Just my 2 cents.  Not  full proof, but pretty close

---

### Post by drsox1899 on 2008-05-20
> **aysiu said:**
> Huh? So you're supposed to click on a link in an email from a bank? No, I totally disagree. Links in email are *the* primary source of phishing scams.

Please, if you believe the search engines won't take you to a proper bank site, give me at least an example of this.

I said by POST or DIRECT CONTACT not email.  Yes of course email is the dumbest.  I had a bad link from a Google search as I was too rushed to look for the letter from my bank.

---

### Post by aysiu on 2008-05-20
What does POST or DIRECT CONTACT mean? Somehow you have to get that to a web browser. Are you typing that in? As I said before, typing can lead to mistyping, which is a fast way to get to phishing sites.

---

### Post by tact on 2008-05-20
> **aysiu said:**
> 
Please, if you believe the search engines won't take you to a proper bank site, give me at least an example of this.


Try this one... 
[http://it.slashdot.org/article.pl?sid=07/11/29/1318257](http://it.slashdot.org/article.pl?sid=07/11/29/1318257)

I have read many reports of bad guys injecting/poisoning search engines to get people to land on their fake servers for the purposes of infecting PC's with malware.   If the example above is not specifically related to a banking scam - sorry.  I don't have the time to google for you for more than 2 minutes.  

If they can do it (subvert search results) - they can do it for bank search results.  If they can do it to install Malware - they can adjust the attack so that the site you get directed to LOOKS like your bank homepage...."Please enter your password...pwned!"

Now assuming you actually find yourself connected to YOUR bank's REAL site:  Even the legit BANK site can be poisoned - there were reports earlier this year that a bank in India was serving up about a hundred different types of malware because it had been compromised.    If they can do that - why not install keyloggers and password sniffers that "call home".

But don't let paranoia stop there.  You use an ATM?  THAT must be safer right?

In the UK a gang rented a shop front.  Installed an ATM they bought from a scrap auction and renovated to look like a current ATM.  

Inside the ATM was just a laptop set up to produce a set of screens that LOOK like the prompts/screens of a real ATM, and record all the card data and PIN numbers entered.  

Of course every transaction ended with the "Cannot dispense cash right now - Transaction Cancelled" message.   

The ruse was only exposed when a customer eventually complained to the bank how their new ATM at [location] never NEVER has cash!   hehehe

Soooooo...  just don't worry!  hehe.  My bank gives me terms and conditions that say that provided I never expose my PIN number I will never be responsible for losses.

Cheers

---

### Post by jrusso2 on 2008-05-20
> **BXA121 said:**
> Im quite reserved about using my banking information over the internet. Whenever i have ever needed to deal with my monies, ive always spoken to a person 1 on 1, i have never used telephone or the internet to bank. 

I know it can be unsafe and there is risk of my info being taken off me as it has been demonstrated by past "cock ups" heard from the news etc. 

how safe is online banking, does it matter if the OS is windows or ubuntu? Can my information still be exploited once it leaves my computer?

How does one make their system secure to do online banking?

Any ideas?

I stopped using on line banking years ago because its unsafe. No matter how careful and secure I am on this end the security is only as good as the banks.  A weak website, unpatched security issues, there are numerous ways to break into a bank and people all over the world got nothing better to do then to sit there and hammer on them.

Now I tell them I won't be using online banking don't even give me a login.

---

### Post by drsox1899 on 2008-05-20
> **aysiu said:**
> What does POST or DIRECT CONTACT mean? Somehow you have to get that to a web browser. Are you typing that in? As I said before, typing can lead to mistyping, which is a fast way to get to phishing sites.


POST = person comes to your house with an object called an envelope inside which is a letter from your bank with your bank codes and login site etc information.

DIRECT CONTACT = visiting a building called a BANK where one meets with a human to establish eligibility for them handling your funds via non-paper means.

---

### Post by hyper_ch on 2008-05-20
I use only one account for online banking. The one I get my monthly wage paid to... so I just login there, pay the bills, move the rest of the money to my savings account and that's it.

There's never much money on that account and it can't get into a negative saldo... worst case: I loose a monthly wage - it would be annoying but serious...

---

### Post by tact on 2008-05-20
> **drsox1899 said:**
> POST = person comes to your house with an object called an envelope inside which is a letter from your bank with your bank codes and login site etc information.

DIRECT CONTACT = visiting a building called a BANK where one meets with a human to establish eligibility for them handling your funds via non-paper means.

Supported.   And hand typing this into a "create bookmark" text entry field, just once, carefully, then tested to ensure none of the typos that aysiu is worried about... gotta be the best way to avoid being sent to a fake site.

But as I mention - even you arrive at the legit bank site.  Has it been poisoned?  Who knows.  hehehe....  use the fake ATM down the street instead!

Nothing is guaranteed secure so don't go there.  All we can say is that some habits will be MUCH more likely to get you burned - like clicking links in emails or even search engines.  

No need to stop using the technology either - the banks want your custom and will take the risk of fraud (giving you committment to suffering NO LOSS unless you divulge your PIN) just to get you as their customer.  For now.

---

### Post by hyper_ch on 2008-05-20
well, you can't burn yourself if you make use of private banking and go to the teller with a person behind ;)

Only if you get money from the bank and then leave the building you might get robbed...

---

### Post by pietjanjaap on 2008-05-20
Install linux,
then install vmware,
install a fresh ubuntu in vmware,
use this install only for banking,
before you go banking always manual update,
don't install other software.

---

### Post by leexgx on 2008-05-21
i cant even remember what most bank websites names are 
 
as long as your close to what is typed into search engine the top one is norm right (never click on sponsored links norm yellow at the top or/and the right of the page)
 
in any case on ubuntu is safe to use official banking web sites
 
basically all online banking problems are due to users clicking on links in emails or miss spelling there real banking web site (why search google/yahoo is an good idea until your browser has cached it) and then filling info in that they should not
 
in the UK basically no web site is using the RSAkeys yet so its very easy if you been duped into an web site (and not so bright in telling not the real one) that wants all of your security details instead of parts of it (no bank will ever ask for your credit card details or account and sort code or all of your security details or send you emails asking for them)

---

