---
title: "Ubuntu guide website"
date: 2012-11-10
forum: The Cafe
---

### Post by jsvidyad on 2012-11-10
Hello,

   Someone gave me the location of this website: [www.ubuntuguide.org](www.ubuntuguide.org)

Is this a trustworthy website? They have given a sample apt repository sources list here : [http://ubuntuguide.org/wiki/Ubuntu_Precise_Repositories#Edit_the_repository_sources_list](http://ubuntuguide.org/wiki/Ubuntu_Precise_Repositories#Edit_the_repository_sources_list)


   Can someone please take a look at that list of repositories in the link I gave above and tell me if I can safely add those repos to my /etc/apt/sources.list or maybe even replace my current /etc/apt/sources.list with the repos given on that link above?

---

### Post by uclugLee on 2012-11-10
I can't speak for the repository list, but the official Ubuntu documentation in here:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by jsvidyad on 2012-11-11
Does anyone know anything about the website i mentioned in my post?

---

### Post by 2F4U on 2012-11-11
And what is the reason for using that sources.list? What do you intend to achieve?

---

### Post by jsvidyad on 2012-11-11
Someone gave me the link to that site and told me that it is an un-official guide for linux. That's why I'm asking all this.

---

### Post by 2F4U on 2012-11-11
Basically, you already answered your own questions. The site is unofficial and so are some of the repositories, meaning not supported by Ubuntu. It is mostly up to you if you trust the site and the repositories, because nobody can guarantee now and in the future that there won't be problems.

---

### Post by oldos2er on 2012-11-11
> **jsvidyad said:**
> Someone gave me the link to that site and told me that it is an un-official guide for linux. That's why I'm asking all this.

Yes, it's unofficial, but ubuntuguide.org is a good site for info, in my opinion. 

The repository [http://packages.medibuntu.org/](http://packages.medibuntu.org/) is the same one you get when you visit medibuntu.org; the google repo is installed when you install one of google's deb files for Chrome or GoogleEarth.

---

### Post by jsvidyad on 2012-11-11
> The repository [http://packages.medibuntu.org/](http://packages.medibuntu.org/) is the same one you get when you visit medibuntu.org; the google repo is installed when you install one of google's deb files for Chrome or GoogleEarth. 

So, you think the repositories in the apt sources.list given on that website are trustworthy?

---

### Post by deadflowr on 2012-11-11
> **jsvidyad said:**
> So, you think the repositories in the apt sources.list given on that website are trustworthy?

Their as trustworthy as any repo you add. Whether a ppa or through editing a source.list.
The page is a wiki though, so anyone can add a bad repo, but at the same time anyone can also remove it.
Bad repos and packages become known quickly.

---

### Post by jsvidyad on 2012-11-23
> **oldos2er said:**
> Yes, it's unofficial, but ubuntuguide.org is a good site for info, in my opinion. 

The repository [http://packages.medibuntu.org/](http://packages.medibuntu.org/) is the same one you get when you visit medibuntu.org; the google repo is installed when you install one of google's deb files for Chrome or GoogleEarth.

Hello, I am mainly concerned about the medibuntu and google repositories as the other repositories are already there when we install ubuntu(with the gb in the repository urls replaced with us of course). So, you think the medibuntu and google repositories given there are reliable? I have heard that medibuntu is a really solid repository with packages that are not distributed with the official ubuntu repositories. 
   I am mainly concerned about the repositories for kubuntu 10.04 and ubuntu 12.04. I will give the corresponding repositories shown on the ubuntu guide web sites([http://ubuntuguide.org/wiki/Ubuntu:Lucid#Manually_add_repositories](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Manually_add_repositories) and [http://ubuntuguide.org/wiki/Ubuntu:Precise#Manually_add_repositories](http://ubuntuguide.org/wiki/Ubuntu:Precise#Manually_add_repositories)). Can you please tell me if they correspond to the actual medibuntu repositories for those ubuntu/kubuntu versions and are not fake ones designed to get us to install malicious packages?

ubuntu 12.04
____________
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free

kubuntu 10.04
_____________
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

   

Thank You in advance for your help.

---

### Post by oldos2er on 2012-11-23
> **jsvidyad said:**
> I will give the corresponding repositories shown on the ubuntu guide web sites([http://ubuntuguide.org/wiki/Ubuntu:Lucid#Manually_add_repositories](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Manually_add_repositories) and [http://ubuntuguide.org/wiki/Ubuntu:Precise#Manually_add_repositories](http://ubuntuguide.org/wiki/Ubuntu:Precise#Manually_add_repositories)). Can you please tell me if they correspond to the actual medibuntu repositories for those ubuntu/kubuntu versions and are not fake ones designed to get us to install malicious packages?

ubuntu 12.04


Didn't I answer this already? You can easily check for yourself at medibuntu.org and [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)

---

### Post by jsvidyad on 2012-11-24
> Didn't I answer this already? You can easily check for yourself at medibuntu.org and [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)


Hello, I read your previous post. What I understand from that post of yours is that [http://packages.medibuntu.org/](http://packages.medibuntu.org/) is the url/location for the genuine medibuntu repository. Did I understand you correctly?

---

### Post by oldos2er on 2012-11-24
Yes.

---

### Post by jsvidyad on 2013-03-28
Hello,

   I know this thread has been inactive for some time. In the next couple of days, I am going to upgrade some ubuntu/kubuntu 10.04 machines to ubuntu/kubuntu 12.04(still haven't decided whether to do a fresh install or upgrade via internet). Anyway, I wanted to confirm that [http://packages.medibuntu.org/](http://packages.medibuntu.org/) is still the url for the genuine medibuntu repository. I am concerned that the url for the genuine medibuntu repository might have changed in the meantime. Can someone let me know whether the above url is still the url of the genuine medibuntu repository or if it has changed. If it has changed, can you please also give me the new url for the genuine medibuntu repository?

---

### Post by oldos2er on 2013-03-28
> **jsvidyad said:**
>  Anyway, I wanted to confirm that [http://packages.medibuntu.org/](http://packages.medibuntu.org/) is still the url for the genuine medibuntu repository. 

It is.

---

### Post by jsvidyad on 2013-03-29
Ok. Thanks for the prompt and helpful reply.

---

### Post by jsvidyad on 2013-05-04
Hello,

   I put off upgrading my systems to ubuntu 12.04 when I got to know that  ubuntu/kubuntu 10.04 was going to be supported till May 9th. Anyway I am doing the upgrades on Monday. I am going to use a fresh install of ubuntu 12.04. Once again, I'd like to confirm that [http://packages.medibuntu.org/](http://packages.medibuntu.org/) is still the url for the genuine medibuntu repository. Sorry to ask again, but I was worried it might have changed in the meantime.

---

### Post by jsvidyad on 2013-05-06
Can someone please help me here?

   - Thank You.

---

### Post by jsvidyad on 2013-05-07
Hello,

  Still hoping someone can help me.

---

### Post by jsvidyad on 2013-05-07
> **lovebluesky2009 said:**
> if you have no other choice&#65292;you can choose this one

I don't understand what you are trying to say.

---

### Post by oldos2er on 2013-05-07
I really don't understand why you're still asking this question. Medibuntu is medibuntu; however it's no longer [actively maintained]("http://www.medibuntu.org/getinvolved.php"). Whether you choose to trust it or not is up to you.

---

### Post by jsvidyad on 2013-05-07
> **oldos2er said:**
> I really don't understand why you're still asking this question. Medibuntu is medibuntu; however it's no longer [actively maintained]("http://www.medibuntu.org/getinvolved.php"). Whether you choose to trust it or not is up to you.

Hello, 
   I was just worried that the url for the medibuntu repository might have changed from [http://packages.medibuntu.org/](http://packages.medibuntu.org/) in the time since I last asked about it. That's why I asked if it has changed or not. If the medibuntu repsository is unmaintained, is it a good idea to add it to my /etc/apt/sources.list file? The packages might be old and might have security issues, right?

---

### Post by oldos2er on 2013-05-08
> **jsvidyad said:**
>  The packages might be old and might have security issues, right?

That's possible.

---

### Post by jsvidyad on 2013-05-08
But the url for the medibuntu repository is still [http://packages.medibuntu.org/](http://packages.medibuntu.org/) , right?

---

### Post by jsvidyad on 2013-06-07
Hello,

  An earlier post in this thread mentioned that the medibuntu repository was not being actively maintained. So, has the url for the genuine medibuntu internet repository changed or is it still [http://packages.medibuntu.org/](http://packages.medibuntu.org/) ? I am concerned that the url might have changed to a different one. By url, I mean the url that I have to add to the sources.list file in order to use the medibuntu repository on my computer.

---

### Post by ronnyroll on 2013-06-08
> **uclugLee said:**
> I can't speak for the repository list, but the official Ubuntu documentation in here:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
content of both are very similar.

---

### Post by Bucky Ball on 2013-06-08
*Thread moved to **The Cafe**.*

***Reason:*** Not technical support request.

---

