---
title: "Barracuda Networks Enlists Open Source Community In Trend Micro Patent Fight"
date: 2008-01-31
forum: The Cafe
---

### Post by PartisanEntity on 2008-01-31
> The e-mail and Web security firm is asking the open source community to provide information that can invalidate Trend Micro's patent on gateway antivirus scanning.

...

Barracuda Networks, a maker of e-mail and Web security hardware, has sent out a distress call to the open source community to save it from patent litigation at the hands of Trend Micro, a competing security company. On Tuesday it asked for help from anyone who can provide information that can invalidate Trend Micro's patent on gateway antivirus scanning.

Barracuda Networks has framed the dispute as an attack not only on itself but on the open source community and the free Clam AntiVirus software by "commercial patent holders attempting to unjustly hinder the free and open source community," as Dean Drako, president and CEO of Barracuda Networks, put it in a statement issued on Tuesday.

Trend Micro spokesperson Mike Sweeny said the litigation isn't an attack on the open source community. "This case is really about two companies, Barracuda Networks and Panda Security, that are selling products in the U.S. that we feel infringe on our time-tested patent," he said. Drako disagrees with this assessment. "If you read the legal documents from Trend Micro, all of the infringement claims they make are about Clam AV," he said in a phone interview. "They may be legally suing us but ... it's pretty clearly an attack on Clam AV." 

[Continued]("http://www.informationweek.com/news/showArticle.jhtml?articleID=206100073")

The patent in question: [http://www.freepatentsonline.com/5623600.html](http://www.freepatentsonline.com/5623600.html)

---

### Post by bufsabre666 on 2008-01-31
thats really something that sound important and maybe, just maybe, shouldnt be something that just one company has the ability to do

---

### Post by stoodleysnow on 2008-01-31
Suggestion to judge: throw out Trend Micro's case. They haven't got a leg to stand on.

---

### Post by PartisanEntity on 2008-01-31
Unfortunately, Trend Micro's patent is so vague, that in a strictly legal sense they may have a foot to stand on. Morality and ethics often have little to do with the law.

---

### Post by popch on 2008-01-31
The patent restricts itself to scanning files transmitted between network nodes using (t)ftp.

I suspect that virus detection by placing a file into a temporary location, then scanning for a virus and then moving the scanned file into the desired location was 'invented' before that patent was filed. That would constitute 'prior art', I think.

Hence, the patent only states that a 'prior invention' also was applicable if the file was transferred from another network node using two variants of a particular protocol. 

Since the 'prior invention' is applicable to any method in which a new files happens to arrive at the node, the new patent appears not to state anything new.

I think it should not be all that difficult to document whether virus scanning in generel was already current practice before that patent was applied for. Also, it should not be difficult to show that this particular patent demonstrates only a trivial special case of 'virus scanning' in general.

If push comes to shove, competitors could always use HTTP to transfer the file to be scanned from localhost to localhost and scan it upon receiving from HTTP. In that case the original patent would not apply because it names FTP and TFPT only as transmission methods.

Caution: I am not a lawyer and in particular, I am not familiar with US patent law. The above comments rely on 'common sense' which may or may not apply here.

---

