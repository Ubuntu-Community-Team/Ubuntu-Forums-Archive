---
title: "Since credit cards existed before 1969, doesn't that mean so did Internet?"
date: 2011-06-02
forum: The Cafe
---

### Post by brawnypandora0 on 2011-06-02
Since there were magnetic stripes on credit cards before 1969, doesn't that mean there already was an Internet system that automatically connected determined at the point of purchase whether a credit card is approved for sale or not?

Also, do modern day debit card systems use Internet for connecting to people's bank accounts?

---

### Post by speedwell68 on 2011-06-02
No and no.

---

### Post by 3Miro on 2011-06-02
Most places today use phones for credit cards, i.e. a machine calls the Bank's automated system.

In the early 2000 I saw places in the US that would take an imprint of the card and not have a phone system.

First credit cards were issues only to select few people, the business would take information off the card at the time of purchase and get the money from the Bank afterwards. If they wanted to verify the amount, then they could call the Bank (assuming they had phones).

Credit Cards are in no way dependent on or associated with the Internet.

---

### Post by KiwiNZ on 2011-06-02
They used an imprinter device to copy the card details onto a sales slip

---

### Post by 1clue on 2011-06-02
I just had my card processed yesterday with a manual imprinter, in a fairly populated part of the USA.  When there's a computer problem they have no problem using an imprinter, but some of the teenagers have trouble figuring out how to do it.

FWIW, the card reader doesn't call the bank.  It calls a credit card processing network, which the bank subscribes to.  Look on the back of your card, you see logos for networks the card works directly with:  Instant Cash, Pulse, Cirrus, Star, etc.  Those networks are separate institutions and there are hundreds or thousands of them.  Each has some number of agreements with other networks which govern how the partner network charges for services.

Regardless, even if the credit card network uses identical equipment it definitely does not use the wide open Internet to process financial data. If they've switched to any sort of Internet technology they are doing so on a completely separate network.

---

### Post by 3Miro on 2011-06-02
> **KiwiNZ said:**
> They used an imprinter device to copy the card details onto a sales slip

Awesome picture. I have seen those in the early 2000s.

You can also copy the numbers by hand.

---

### Post by FuturePilot on 2011-06-02
> **KiwiNZ said:**
> They used an imprinter device to copy the card details onto a sales slip

That thing brings back memories.

---

### Post by Old_Grey_Wolf on 2011-06-02
> **brawnypandora0 said:**
> Since there were magnetic stripes on credit cards before 1969, doesn't that mean there already was an Internet system that automatically connected determined at the point of purchase whether a credit card is approved for sale or not?

No.

In 1969, very few if any points-of-sale; such as, petrol (gas) stations, chemists (pharmacies), etc., had a computer. They didn't have Internet connections until much later.

In the 1960's, 1970's, 1980's, and into the 1990's, they used these:
> **KiwiNZ said:**
> They used an imprinter device to copy the card details onto a sales slip

---

### Post by uRock on 2011-06-02
> **Old_Gray_Wolf said:**
> No.

In 1969, very few if any points-of-sale; such as, petrol (gas) stations, chemists (pharmacies), etc., had a computer. They didn't have Internet connections until much later.

In the 1960's, 1970's, 1980's, and into the 1990's, they used these:

Yup, I remember gas stations in the 80's that only accepted cash and check, but only if they had your name and address on file could you then use a check.

---

### Post by sammiev on 2011-06-02
I remember taking credit cards in the 70's when I was working pumping gas. :)

---

### Post by alphacrucis2 on 2011-06-02
> **Old_Gray_Wolf said:**
> No.

In 1969, very few if any points-of-sale; such as, petrol (gas) stations, chemists (pharmacies), etc., had a computer. They didn't have Internet connections until much later.

In the 1960's, 1970's, 1980's, and into the 1990's, they used these:

In this country eftpos terminals are connected up to completely separate private networks that have no connection to the internet. Also proprietary data networks were around long before the internet.

---

### Post by CTBuckweed on 2011-06-02
> **brawnypandora0 said:**
> Since there were magnetic stripes on credit cards before 1969, doesn't that mean there already was an Internet system that automatically connected determined at the point of purchase whether a credit card is approved for sale or not?

Also, do modern day debit card systems use Internet for connecting to people's bank accounts?

In answer to your question, yes, sometimes, the internet is used. ATM machines are able to use wireless connections for communicating to the processing switch. Traditionally, the connections are over dial-up POTS lines. Some high density ATMs (mainly casinos with several ATMs) will use a single physical connection to send requests to the switch. This can be a poll/select protocol with an on-site controller to poll the ATMs. ATM traffic must be secured from prying eyes so the traffic is encrypted over a VPN.

A typical message flow from an ATM to your bank consists of several hops. The ATM connects to a processor/switch whose sole function is to service connections and transactions from ATMs. The deployer/owner of the ATMs has a business agreement with the processor.. The processor, in turn, maintains connections with one or more national financial networks. It chooses which national network to use and routes the request. Then the transaction gets routed on to your bank for approval/denial. All this routing is based on the ISO/BIN (the first few digits) on the card.

The links from the ATM switch to the national networks are typically accomplished by a dedicated point to point link or an X.25 frame relay connection.

I have worked in the ATM industry for about 20 years. I was with companies that created and sold ATM processing software & services.

---

### Post by Dr. C on 2011-06-02
Credit cards were for the most time an off line payment system until the 1990's. Merchants would use an imprinter and the credit card companies would send the merchants a paper bulletin of canceled cards. For larger transactions the merchant would phone for authorization. Then came dial up terminals  which would literally dial up with a modem over a telephone line for each transaction, and were very annoying when waiting in line, especially to those of us who knew what was going on.

---

### Post by pookiebear on 2011-06-03
We had a Sears and a JCpenny card back in late 70s. All done with Imprinter. MY wife has an imprinter she still uses when she is selling stuff at craft fairs. They are still accepted. 
Paypal credit card processing will still accept an imprinted sales slip. Many others do too. You can type in the amounts in batches for the deposits and mail a whole bunch of them in at the end of the month, or scan them in now.

---

### Post by brawnypandora0 on 2011-06-03
> **CTBuckweed said:**
> In answer to your question, yes, sometimes, the internet is used. ATM machines are able to use wireless connections for communicating to the processing switch. Traditionally, the connections are over dial-up POTS lines. Some high density ATMs (mainly casinos with several ATMs) will use a single physical connection to send requests to the switch. This can be a poll/select protocol with an on-site controller to poll the ATMs. ATM traffic must be secured from prying eyes so the traffic is encrypted over a VPN.

A typical message flow from an ATM to your bank consists of several hops. The ATM connects to a processor/switch whose sole function is to service connections and transactions from ATMs. The deployer/owner of the ATMs has a business agreement with the processor.. The processor, in turn, maintains connections with one or more national financial networks. It chooses which national network to use and routes the request. Then the transaction gets routed on to your bank for approval/denial. All this routing is based on the ISO/BIN (the first few digits) on the card.

The links from the ATM switch to the national networks are typically accomplished by a dedicated point to point link or an X.25 frame relay connection.

I have worked in the ATM industry for about 20 years. I was with companies that created and sold ATM processing software & services.

So it's basically all done over phone lines? How are supermarkets with multiple transactions every few seconds able to handle this? Multiple lines?

Also, what would cause the system to go down? How is it fixed?

---

### Post by jtarin on 2011-06-03
I can remember pumping gas in the 60's and handwriting the form. It was when Esso became Exxon  in the U.S.

---

### Post by whatthefunk on 2011-06-03
In a lot of the world even today they dont have the swiping machines.  A lot of places dont even have the imprinters and instead the guy behind the register will take a piece of paper and a crayon and make a rubbing of your credit card.

---

### Post by Bandit on 2011-06-03
> **brawnypandora0 said:**
> Since there were magnetic stripes on credit cards before 1969,...........

> **KiwiNZ said:**
> They used an imprinter device to copy the card details onto a sales slip

Thanks KiwiNZ, guess most people didnt realise there is more then just one reason the numbers and card holders name has raised lettering..

---

### Post by LowSky on 2011-06-03
> **uRock said:**
> Yup, I remember gas stations in the 80's that only accepted cash and check, but only if they had your name and address on file could you then use a check.

I remember when you could pump first then pay. Now they are all afraid of people pump and ditching you need to pay first. I guess that happens when gas costs quadruple in 10 years.

I do find it funny when young people accept that credit cards look exactly the same in the 1960's as they do in 2011.

---

### Post by 3rdalbum on 2011-06-03
> **Bandit said:**
> Thanks KiwiNZ, guess most people didnt realise there is more then just one reason the numbers and card holders name has raised lettering..

Mine doesn't, but then mine is prepaid. You obviously can't use it in an imprinter, and I don't believe imprinters are in use in Australia anymore. Ever.

Somebody earlier said that ATMs used VPN tunnels to communicate information to the bank... well, you'd be horrified to hear this, but some ATMs transmit your card details in cleartext.

---

### Post by Gerontion on 2011-06-03
I'm amazed by (a) how short cultural memory is and (b) how old this thread has made me feel.

---

### Post by Swagman on 2011-06-03
> **LowSky said:**
> I remember when you could pump first then pay. Now they are all afraid of people pump and ditching you need to pay first. I guess that happens when gas costs quadruple in 10 years.

I do find it funny when young people accept that credit cards look exactly the same in the 1960's as they do in 2011.

lol

The cost of fuel in the UK is a damn sight more expensive than the U.S but we can still fill up first and then pay.

Believe it or not there are still some places here and in Australia that use "Honesty boxes" But not for fuel admittedly.

---

### Post by SeijiSensei on 2011-06-03
Might I suggest reading up a little on the history of the Internet?  The [Internet Society](http://www.isoc.org/) is a good place to start.  You could also take a look at [STD0003](http://www.rfc-editor.org/rfc/std/std3.txt), which I'll point out has a date of October, 1989.

---

### Post by Laforge129 on 2011-06-03
> **speedwell68 said:**
> No and no.

I can attest to that!!  I work with cards all day long!!

---

### Post by JKyleOKC on 2011-06-03
I have an imprinter on my desk here, together with a stack of sales slips and refund slips. I only use them when a client asks for a receipt; all of my data recovery work comes in via the Internet and gets delivered the same way so I never actually see the card. The customer sends me the appropriate data via fax or phone (I discourage using Email since it's not at all secure), and I pass it on to my bank via a touch-tone telephone system. Works great for international transactions, which are half or more of my total business.

Some 25 years ago I had a retail popcorn shop, and there we used an imprinter on a daily basis. At that time, the "merchant copy" of the sales slip just went to my bank as if it were a check. No electronics at all were involved!

---

### Post by mips on 2011-06-03
> **3Miro said:**
> Awesome picture. I have seen those in the early 2000s.

You can also copy the numbers by hand.

Or just put the paper slips above the card and holding firmly so nothing moves rub the sides of a pen over it for the details on the card to be transferred to the paper :D

---

### Post by 1clue on 2011-06-04
> **brawnypandora0 said:**
> So it's basically all done over phone lines? How are supermarkets with multiple transactions every few seconds able to handle this? Multiple lines?

Also, what would cause the system to go down? How is it fixed?

What you may not know is that beyond a certain point, plain old telephone goes through hardware which is essentially identical to what carries Internet.  The software is different, and the routing has different priorities to ensure real time delivery, but it's the same basic hardware.  Just not connected.

At my business, we have a T2 for data and a T3 for voice.  Different hardware breaks it into phone lines, but actually inside my company's walls there are two essentially identical services.  This is NOT what you call voice over IP.  We're considering upgrading to that, but the telephones are standard office phones.

Depending on how much data you're moving, you can get a line for voice which is packet-based same as Internet.

Moreover, you can get an Internet-type data line which does not connect to the Internet.  Companies do it all the time.  If security is paramount, you can run your own wires, or you get what's called a permanent virtual circuit, which is a direct data path from one point to the other which is billed per mile and has whatever bandwidth capabilities you're willing to pay for.

---

### Post by brawnypandora0 on 2011-06-25
So is an ATM transaction the same in terms of the principles of the network? That is, not needing Internet?

---

### Post by CTBuckweed on 2011-06-26
> **brawnypandora0 said:**
> So is an ATM transaction the same in terms of the principles of the network? That is, not needing Internet?

ATMs need to communicate with the card holder's financial institution somehow. Be it internet, a POTS phone line, or even a salty shoe-string that's kept damp for conductivity.

---

### Post by Gremlinzzz on 2011-06-26
credit was much simpler back then,they give you credit and send Bruno around to collect.
either the money or what you got on credit:D

---

### Post by haqking on 2011-06-26
> **Gremlinzzz said:**
> credit was much simpler back then,they give you credit and send Bruno around to collect.
either the money or what you got on credit:D

still happens, i was talking to bruno the other day ;-)

---

### Post by beniwtv on 2011-06-27
> **JKyleOKC said:**
> The customer sends me the appropriate data via fax or phone (I discourage using Email since it's not at all secure)

Hate it to rain down on your parade... but fax or phone is about as secure as e-mail. For credit card information, neither fax, phone or e-mail cuts it. Use SSL / encryption.

Just sayin'.

---

### Post by JKyleOKC on 2011-06-27
> **beniwtv said:**
> fax or phone is about as secure as e-mail.Of course the professional spooks can tap into just about anything, but both fax and phone are essentially direct connections between point A and point B rather than routing, in the clear, between any number of servers along the way. As such, they offer much less opportunity for interception by the average script kiddie. Anything that uses the Internet is vulnerable to a man-in-the-middle attack; direct point-to-point contacts are not so much so.

---

### Post by walt.smith1960 on 2011-06-27
> **LowSky said:**
> **I remember when you could pump first then pay. Now they are all afraid of people pump and ditching you need to pay first. I guess that happens when gas costs quadruple in 10 years.**

I do find it funny when young people accept that credit cards look exactly the same in the 1960's as they do in 2011.

There are a lot of places where you can still pump first then pay.  Just not in NY--or S.E. PA.

---

### Post by Paqman on 2011-06-27
> **Gerontion said:**
> I'm amazed by (a) how short cultural memory is and (b) how old this thread has made me feel.

This. People will be asking questions like this about cheques in a few years.

---

### Post by beniwtv on 2011-06-27
> **JKyleOKC said:**
> Of course the professional spooks can tap into just about anything, but both fax and phone are essentially direct connections between point A and point B rather than routing, in the clear, between any number of servers along the way. As such, they offer much less opportunity for interception by the average script kiddie. Anything that uses the Internet is vulnerable to a man-in-the-middle attack; direct point-to-point contacts are not so much so.

Nope, phone lines are routed through various centrals, analog switches, cabling, etc... along the way, sometimes even over the Internet depending on your destination. It's not really point A to point B. 

Man-in-the-middle attacks can only be prevented by using encryption. Relying on clear protocols _never_ is secure.

That being said, your communications being intercepted amongst the millions is slim at best, and this is only an advise, never trust any type of open connections.

---

### Post by 1clue on 2011-06-27
Man in the middle attacks are only reliable if you're on a guaranteed route between the points.  There are relatively few choke points on the Internet.  It's not a cloud exactly, but there are diverse routes in case one goes down.

As well, if you suspect your "man in the middle" is the government of whatever country you're in, then chances are you don't have much chance to protect yourself even if you do have encryption.

---

### Post by lisati on 2011-06-27
> **KiwiNZ said:**
> They used an imprinter device to copy the card details onto a sales slip

Ah, the "zip zap" machine. I nearly scored a free lunch once after turning up at a cafe during a break in the filming of a commercial.
([This]("http://www.filmarchive.org.nz/sellebration/view.php?id=226") isn't the actual commercial, but is part of the same campaign.)

---

### Post by SoFl W on 2011-06-27
I remember when ATM first started getting popular they were all modem  based.  Some time during the night the ATM would dial up the central  office and exchange data.  The branch ATM had no idea if you already  withdrew your daily limit at another location.  People would go from  branch to branch withdrawing the maximum amount from each ATM branch.   The problem wasn't discovered until the machines synced that night.


> **CTBuckweed said:**
> In answer to your question, yes, sometimes, the internet is used. ATM machines are able to use wireless connections for communicating to the processing switch.

I have worked in the ATM industry for about 20 years. I was with companies that created and sold ATM processing software & services.


You worked in the ATM industry for 20 years and wrote "ATM MACHINE?"

---

### Post by eveg on 2011-06-27
am i wrong or did the old ones, 1980's and before, not have mag strips at all? imprint was proof of actual card purchase rather than invention/fraud on seller's part, and the physical receipts were daily stuff of business, in the zipup envelope of a register at the end of the day w/ the paper checks and all. atm cards only worked at the bank and credit cards, no debit, at the store...

---

### Post by eveg on 2011-06-27
> **SoFl W said:**
> I remember when ATM first started getting popular they were all modem  based.  Some time during the night the ATM would dial up the central  office and exchange data.  The branch ATM had no idea if you already  withdrew your daily limit at another location.  People would go from  branch to branch withdrawing the maximum amount from each ATM branch.   The problem wasn't discovered until the machines synced that night.





You worked in the ATM industry for 20 years and wrote "ATM MACHINE?"

yeah, a bit redundant, like 'usb bus'

---

### Post by JKyleOKC on 2011-06-27
Or personal PIN number...

---

### Post by sammiev on 2011-06-27
> **SoFl W said:**
> I remember when ATM first started getting popular they were all modem  based.  Some time during the night the ATM would dial up the central  office and exchange data.  The branch ATM had no idea if you already  withdrew your daily limit at another location.  People would go from  branch to branch withdrawing the maximum amount from each ATM branch.   The problem wasn't discovered until the machines synced that night.

We were dial up till a year a go and when you with drew your amount you were done. It maybe the country you are in but in Canada you were done. GL :)

---

### Post by doas777 on 2011-06-27
> **lisati said:**
> Ah, the "zip zap" machine. 
we called em knuckle-busters. 

@op: the internet can be said to have come into existance in the early ninties, when legislation drafted by Al Gore granted public and commercial access to the former NSFNet (National Science Foundation).

---

### Post by SoFl W on 2011-06-27
> **sammiev said:**
> We were dial up till a year a go and when you with drew your amount you were done. It maybe the country you are in but in Canada you were done. GL :)

This was 25-30+ years ago.  People would go from branch to branch.

---

### Post by 1clue on 2011-06-28
OMFG.

Al Gore had absolutely nothing to do with the Internet.  It was over a decade old by the time Gore had anything to do with it, and then he was just another cog in the wheel.

I remember when that bill was on the floor.  We made jokes about it, but I think we all wanted it to pass.  I remember using the net before that from my school.

Saying Al Gore invented the Internet is like saying U.S. President Dwight Eisenhower invented rockets by announcing intent to go into space, after a millenia of Chinese fireworks, WW2 German rockets and after Sputnik was already orbiting.  Eisenhower was not obtuse enough to make any such claim, but Gore is as daffy as it gets.

---

### Post by doas777 on 2011-06-28
> **1clue said:**
> OMFG.

Al Gore had absolutely nothing to do with the Internet.  It was over a decade old by the time Gore had anything to do with it, and then he was just another cog in the wheel.

I remember when that bill was on the floor.  We made jokes about it, but I think we all wanted it to pass.  I remember using the net before that from my school.

Saying Al Gore invented the Internet is like saying U.S. President Dwight Eisenhower invented rockets by announcing intent to go into space, after a millenia of Chinese fireworks, WW2 German rockets and after Sputnik was already orbiting.  Eisenhower was not obtuse enough to make any such claim, but Gore is as daffy as it gets.


al gore never said he invented the internet. throughly debunked on snopes:
[http://www.snopes.com/quotes/internet.asp](http://www.snopes.com/quotes/internet.asp)

gore specifically said:
> "[FONT=Trebuchet MS,Bookman Old Style,Arial][SIZE=3][COLOR=#000000][FONT=Verdana][SIZE=2&quot;]During  my service in the United States Congress, I took the initiative in  creating the Internet. I took the initiative in moving forward a whole  range of initiatives that have proven to be important to our country's  economic growth and environmental protection, improvements in our  educational system.  [/SIZE][/FONT][/COLOR][/SIZE][/FONT]"

the **Internet** is not **DARPANET**, nor is is **NSFNet**. those were millitary and collegiate networks with access restricted to only specific parties.

The *Information Infrastructure and Technology Act of 1992  *co-sponsored by al gore allowed and funded public access to the then governmentally controlled Internet.
[https://w2.eff.org/Legislation/Bills_by_name/Old/info_infra_tech_s2937_92_gore.bill](https://w2.eff.org/Legislation/Bills_by_name/Old/info_infra_tech_s2937_92_gore.bill)

in fact, even Vint Cerf, co-designer of the TCP/IP system vehemently defended Gore's remarks about helping to create the internet, and credits him, saying:
> "While it is not accurate to say that VP Gore invented Internet, he has played a powerful role in policy terms that has supported its continued growth and application, for which we should be thankful." 
--Vint Cerf[http://web.archive.org/web/20000125065813/http://www.mids.org/mn/904/vcerf.html](http://web.archive.org/web/20000125065813/http://www.mids.org/mn/904/vcerf.html)

so, you are posting falsified propaganda, aka lies.

---

### Post by 1clue on 2011-06-28
I'm absolutely not posting propaganda or lies.

IP stands for Internet Protocol.  The term "internet" has been in use since shortly after anyone connected two networks together and thought of a name for the thing that resulted.  Not only were there "internets" out there, but the Internet was already out there.  It referred to the single massive internet that connected all those government institutions together.

While "created" and "invented" do not mean the same thing, Al Gore had no part in either thing when applied to the Internet.  What Al Gore did was what any number of other elected officials did, by voting to allow its public use.  That is neither invention (my bad choice of words) nor creation (which is what he claimed).

Further, that Vint Cerf quote acknowledges Gore's role in neither invention nor creation.  Only expansion of the venue, which is an incredibly smaller role than what Gore actually claimed.

---

### Post by doas777 on 2011-06-28
> **1clue said:**
> I'm absolutely not posting propaganda or lies.

IP stands for Internet Protocol.  The term "internet" has been in use since shortly after anyone connected two networks together and thought of a name for the thing that resulted.  Not only were there "internets" out there, but the Internet was already out there.  It referred to the single massive internet that connected all those government institutions together.

While "created" and "invented" do not mean the same thing, Al Gore had no part in either thing when applied to the Internet.  What Al Gore did was what any number of other elected officials did, by voting to allow its public use.  That is neither invention (my bad choice of words) nor creation (which is what he claimed).

Further, that Vint Cerf quote acknowledges Gore's role in neither invention nor creation.  Only expansion of the venue, which is an incredibly smaller role than what Gore actually claimed.

  
an internet != The Internet. The Internet is what NSFNet became after [Compusrv]("https://secure.wikimedia.org/wikipedia/en/wiki/CompuServe") connected to it as the first comercial ISP.

---

### Post by 1clue on 2011-06-28
> **doas777 said:**
> an internet != The Internet. The Internet is what NSFNet became after [Compusrv]("https://secure.wikimedia.org/wikipedia/en/wiki/CompuServe") connected to it as the first comercial ISP.

When I was in college, we used the term "The Internet" to mean NSFNet, before there was any official term.  We were all taking networking classes, covering routing and inter-network communications, and there was one screaming big example of "an internet" which was bigger than all others.

It became OFFICIAL after CompuServe, but by general acclaim it was already there, and when you said "the internet" nobody misunderstood what you were talking about if they had had any contact with it.

There's a difference between reading about something in a history book and actually being there.  I was there, in the sense that I was using that network in the pursuit of my studies.

---

### Post by saphil on 2011-06-30
We took credit cards in the 70s and carried the slips to the bank as a deposit. No phone modem connection to check cards. We got little booklets with bad cc numbers every week.

---

