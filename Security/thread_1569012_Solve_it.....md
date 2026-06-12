---
title: "Solve it...."
date: 2010-09-06
forum: Security
---

### Post by robinpaschal on 2010-09-06
Hello to all...

I am working in a Firm. All employees using Ubuntu including me. Every employee checking mail from google and other. but when i am opening mail then Admin come to my desk and notify me to don't do again. I am still in doubt because our work is depend upon gmail ids. Every employee have more than 10 fake gmail ids and we manage work with this ids.


So my question is hows they come to know i am available at my gmail id??

---

### Post by Grenage on 2010-09-06
Nobody here is going to help you circumvent company policy.

---

### Post by robinpaschal on 2010-09-06
Ya you are right. I just want to know this is possible or not. Because from my point of view this is impossible but perhaps technology bit me again.

---

### Post by BkkBonanza on 2010-09-06
Why wouldn't it be possible? You're on their network so they can monitor everything. Of course, they can see what you do.

---

### Post by robinpaschal on 2010-09-06
I know this. They can monitor everything.

---

### Post by BkkBonanza on 2010-09-06
You're probably thinking that it's SSL and can't be viewed. 
But that is a myth. In a controlled environment like that it's fairly well known how to circumvent it.

---

### Post by OpSecShellshock on 2010-09-06
There's no expectation of privacy on a workplace network. Many of them tell you that when you sign on to their computers/network.

To be honest, every tutorial I've ever seen for circumventing workplace security policies (on this site and others) leaves a trail like a comet as long as the security staff is watching and knows what to look for. It's just that in most cases they aren't really watching because they rely on their filtering rules too much or lack the staff and expertise to do it right.

---

### Post by BkkBonanza on 2010-09-06
My apologies. I didn't mean circumvent the policies. I meant for the company to be able to circumvent SSL. ie. they can filter the content despite it being SSL.

After I read my comment again I realized it sounded like I meant the opposite.

---

### Post by Rubi1200 on 2010-09-06
Monitoring workplace activities such as using email or internet is commonplace. I worked once at a company which made it clear that ALL our computer activities were being checked; we even had to sign a contract to that effect.
Circumventing such policies is, in many companies, reason enough to terminate your contract.
My advice: don't do it!

---

### Post by rookcifer on 2010-09-06
> **BkkBonaza said:**
> You're probably thinking that it's SSL and can't be viewed. 

Unless the IT dept uses a MITM appliance, they cannot view the SSL connection.  They can, however, see that the employee is sending encrypted data through port X or Y and thus know he is likely trying to circumvent policy.

---

### Post by BkkBonanza on 2010-09-06
Yes, they would have to install MITM software. Since they control all the systems they can insert their own certificates and not even have to get special intermediate ones.

---

### Post by uRock on 2010-09-06
> **Rubi1200 said:**
> My advice: don't do it!
+1 Staying up with email is not worth getting fired over. My bosses have always said, "You are here to work, so get to work."

---

### Post by OpSecShellshock on 2010-09-06
Yep, that's always an important lesson: the stuff at work isn't yours. Of course, I'm mostly interested in getting whatever they're doing to stop. I don't want to necessarily get anyone in trouble. The thought of functioning as a thug for HR really hits my unpleasant spots.

In any case, you don't have to be able to intercept the content of traffic in order to determine that the traffic itself isn't supposed to be happening. In fact, there have been several cases where I'd really, really rather not have known.

---

### Post by robinpaschal on 2010-09-10
The way i am thinking is different. Perhaps all buddy forgot my question. 
I am wondering with it/
There are more than 200 employees in a firm. Only 1 Admin can check i all those??
Second Point, As i wrote at my previous post each and every employee using more than 5 gmail id...Then how can anybody judge the email id is personal or private?

---

### Post by Rubi1200 on 2010-09-10
> **robinpaschal said:**
> The way i am thinking is different. Perhaps all buddy forgot my question. 
I am wondering with it/
There are more than 200 employees in a firm. Only 1 Admin can check i all those??
Second Point, As i wrote at my previous post each and every employee using more than 5 gmail id...Then how can anybody judge the email id is personal or private?
I think you are missing the point made by various people who have posted responses; if you are not supposed/allowed to check personal email during work hours then you are quite possibly in breach of contract by doing so.

Stop worrying about what other people are doing and make sure your behavior is correct.

---

### Post by v1ad on 2010-09-10
i would ssh out. or through a proxy. maybe even web2 doubt it is installed.

---

### Post by uRock on 2010-09-10
+1 Rubi1200

---

### Post by endotherm on 2010-09-10
my guess is that the gmail social features are telling the admin that you are online and available for chat. msn IM does the same thing with integration into outllook (a colored dot indicating whether you are available and online).

they can certianly tell where you go and much of what you do, just by examining your traffic stream, but I think the simpler answer is more likely correct. 

BTW, what kind of business needs each emp to have 10 fake gmail accounts? are you guys in "Super Professional Advertising/Marketing"?

---

