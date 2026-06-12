---
title: "[getdeb.net] Moving to an APT repository - Request For Comments"
date: 2009-03-04
forum: The Cafe
---

### Post by Vadi on 2009-03-04
Republished from: [http://blog.getdeb.net/2009/03/moving-to-apt-repository-request-for.html](http://blog.getdeb.net/2009/03/moving-to-apt-repository-request-for.html)

> One of the most frequently requested features for getdeb.net is the ability to install the packages from a repository. Despite the clear advantages of using a repository there were some issues that made it unsuitable for us.

On the last couple of months most of those issues have been resolved with changes/improvements that will be available on Ubuntu 9.04. With 2 months left for its release this is the right time to reevaluate the change to an APT repository distribution method.

Advantages
- Security / integrity verification for packages (GPG signed repository)
- Automatic updates
- Install multi-package applications with a single click
- Provide packages with additional dependencies not available on the official repositories

Disadvantages
- Updates will be recommended for all packages making hard to apply only specific packages updates
- Faulty packages will have a wider impact
- Installing a package forces a repositories info update (to ensure you will get the latest version installed)
- Reverting to a previous installed version is harder (requires an unusual force version command or Synaptic)

Implementation
The implementation will require some technical changes that will need to be implemented on the next 2 months:
- Database model needs to be simplified (instead of listing files we only need to list package names and provide APT urls)
- A server side mirror selection script must be implemented to redirect APT file requests to available/updated mirrors
- A debian package must be provided to setup the repository, add custom APT config and install the GPG keyring

The decision to change to a repository or keep with the current (.deb) system must be taken, as providing both methods is not an option (release management would be much harder, not enough human resources to handle it).

I would like to see your opinions/suggestions. 

---

### Post by smartboyathome on 2009-03-04
Isn't there a way to set up APT so that it doesn't update packages from a specific repository unless you tell it to? I thought there was.

---

### Post by FuturePilot on 2009-03-04
> **smartboyathome said:**
> Isn't there a way to set up APT so that it doesn't update packages from a specific repository unless you tell it to? I thought there was.

Yes, it's called "pinning". It's described [here]("https://help.ubuntu.com/community/UbuntuBackports#Use%20pinning%20to%20limit%20the%20backports%20repository") using the backports as an example.

---

### Post by Vadi on 2009-03-04
That's reverse, this is done by user on a per-package bases.

Pinning every package in getdeb save for the one you want would be impractical :)

---

### Post by Polygon on 2009-03-04
so....if i add this repo, its going to try to update all the software on my machine that has later versions on getdeb?

---

### Post by zekopeko on 2009-03-04
> **Polygon said:**
> so....if i add this repo, its going to try to update all the software on my machine that has later versions on getdeb?

yup.

---

### Post by Vadi on 2009-03-04
> **Polygon said:**
> so....if i add this repo, its going to try to update all the software on my machine that has later versions on getdeb?

No. Please read, the point is to exactly avoid that, which is why we're working on a solution for this atm.

---

### Post by Yashiro on 2009-03-04
I thought the whole idea of getdeb was that it was for package downloads and not just another repository.

Fix the website, it's pretty terrible but keep it as a package list.

---

### Post by Vadi on 2009-03-04
It won't be 'just another repository'.

Maybe the wording was off, but it will *not* be a repository. It'll still be the website front-end, except all programs, even with multiple packages, will take 1 click to install. Not one per package.

Also, what's wrong with the site? Thoughts welcome because we weren't aware of any.

---

### Post by Yashiro on 2009-03-04
I'll try to phrase my comments in the language of novice user rather than go into it in great depth.

The layout is bad. It's slow, especially generating the homepage. 
Searching is awkward and not prominent enough on the front page.
The lovely brown ubuntu wiki stylings are ugly and will be out of date when 9.10 rolls around.
The layout is like a forum thread. It's heavily cluttered and confusing due to all the red text and horizontal article dividers.
The top lists are not hugely prominent and being on the left is against what most other sites do.
The bright blue donation text is terrible. We get it, but make a cool looking button that people will want to click and even put on their sites for you.

Overly harsh? Probably, but it does look ugly and it's not the useful and efficient site that it could be. Of course, if the idea is to mirror the look of these forums and offer no real benefit that you couldn't provide in a forum thread then it does the job.

---

### Post by binbash on 2009-03-05
> **Vadi said:**
> It won't be 'just another repository'.

Maybe the wording was off, but it will *not* be a repository. It'll still be the website front-end, except all programs, even with multiple packages, will take 1 click to install. Not one per package.

Also, what's wrong with the site? Thoughts welcome because we weren't aware of any.

Then why is the title moving to an apt repository?There is a big difference between 1 click install and repository.How can people comment about this without seein the product?

---

### Post by Polygon on 2009-03-05
so you mean it will just have a bunch of apt:// links? im curious on how that will work without having ubuntu trying to update everything at once, but if it works, cool =)

and yeah the title of the thread is a bit misleading

---

### Post by Vadi on 2009-03-05
> **Polygon said:**
> so you mean it will just have a bunch of apt:// links? im curious on how that will work without having ubuntu trying to update everything at once, but if it works, cool =)

and yeah the title of the thread is a bit misleading

Sorry, I thought people on UF actually read the posts, not titles only :popcorn:

Yes, it would be a bunch of apt: links, and we're trying to work out on how to stop Ubuntu from turning your machine into a full-time beta tester ;)

---

### Post by Vadi on 2009-03-05
> **Yashiro said:**
> I'll try to phrase my comments in the language of novice user rather than go into it in great depth.

The layout is bad. It's slow, especially generating the homepage. 
Searching is awkward and not prominent enough on the front page.
The lovely brown ubuntu wiki stylings are ugly and will be out of date when 9.10 rolls around.
The layout is like a forum thread. It's heavily cluttered and confusing due to all the red text and horizontal article dividers.
The top lists are not hugely prominent and being on the left is against what most other sites do.
The bright blue donation text is terrible. We get it, but make a cool looking button that people will want to click and even put on their sites for you.

Overly harsh? Probably, but it does look ugly and it's not the useful and efficient site that it could be. Of course, if the idea is to mirror the look of these forums and offer no real benefit that you couldn't provide in a forum thread then it does the job.

Thanks!

We know the design sucks, and any new site designs are welcome. After Playdeb's new design is done, we'll be looking at getdeb too.

I'll look into making the top message nicer, it does look out of place. Probably should change the color and move it to a separate *Contributions* page.

---

### Post by smartboyathome on 2009-03-05
> **Vadi said:**
> Sorry, I thought people on UF actually read the posts, not titles only :popcorn:

Yes, it would be a bunch of apt: links, and we're trying to work out on how to stop Ubuntu from turning your machine into a full-time beta tester ;)

How would you install the packages without a repository, then? apt:// links only work with packages in the repo.

---

### Post by Vadi on 2009-03-05
> Implementation
- A debian package must be provided to setup the repository, add custom APT config and install the GPG keyring

User adds repository, doesn't get any of their packages upgraded unless specifically asked by apturl.

---

### Post by Polygon on 2009-03-05
but don't if you add a repository, doesn't that get checked for new updates every time update-manager runs, and then won't it try to upgrade all the packages when it sees there are newer versions on the getdeb repo? or is there a way to force update-manager and everything to not automatically upgrade everything from the getdeb repo

---

### Post by FuturePilot on 2009-03-05
> **Vadi said:**
> User adds repository, doesn't get any of their packages upgraded unless specifically asked by apturl.

> **Polygon said:**
> but don't if you add a repository, doesn't that get checked for new updates every time update-manager runs, and then won't it try to upgrade all the packages when it sees there are newer versions on the getdeb repo? or is there a way to force update-manager and everything to not automatically upgrade everything from the getdeb repo

This is exactly what the link explains that I posted earlier. You can pin an entire repository with a few simple lines in /etc/apt/preferences. Then you can only install packages from that repository if you specifically tell apt to do so. However this requires the user to make this modification, so there must be another way in which the user is not required to do this.

---

### Post by Tryfon on 2009-05-07
> Thanks!

We know the design sucks, and any new site designs are welcome. After Playdeb's new design is done, we'll be looking at getdeb too.

I'll look into making the top message nicer, it does look out of place. Probably should change the color and move it to a separate Contributions page.

I like the Firefox add-ons website very much. You could get probably some ideas from there since the service it provides is similar.

---

