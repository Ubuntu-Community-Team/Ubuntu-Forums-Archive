---
title: "Do I need to worry about privacy with Ubuntu"
date: 2013-12-22
forum: Security
---

### Post by Fuji_in_Japan on 2013-12-22
Hello,

I upgraded to F20 today on my main machine.  The system crashes often so now I am looking at switching to Ubuntu.  I have an Ubuntu server already.

But I am worried about data leakage and spyware such as the Amazon product recommendation software.  Are these still valid concerns?  If so, I may look for another distro for my desktop everyday machine.  I like ubuntu but Fedora was fine also.  I ran Mandriva for years and was very happy with that until they started having issues.

So the only thing holding me back from Ubuntu is privacy.  

Your thoughts are most welcome.  Do I have a valid concern?

Dave

---

### Post by QIII on 2013-12-22
Hello!

You can turn that stuff off in Unity.  You may also use Kubuntu, Lubuntu, Xubuntu, Ubuntu Gnome, etc., which do not have the features to begin with.

It's an overblown issue anyway.  Nothing personal is exposed.

If you are happy with Fedora, you could always just try to solve whatever issues you are having with it.

---

### Post by Fuji_in_Japan on 2013-12-22
Thanks,  I'll try to work through the Fedora problem.  But if I don't get it resolved, I think I'll switch to Ubuntu.

---

### Post by QIII on 2013-12-22
Use what works for you, of course.  But we'd be happy for you to join the crowd if you end up doing that!

I split my time fairly evenly between Kubuntu and the KDE spin of Fedora because I like both.

---

### Post by craig10x on 2013-12-22
Keep in mind, of course, that you can easily shut off online searches in the "dash" by going to privacy settings and turn the switch off...takes 5 seconds and done ;)
Then all you get in the search is the stuff on your system...

as QIII mentioned, even with it on, nothing personal is exposed...i turn mine off because i find it clutters the dash search too much...
Canonical does get some revenue that helps ubuntu development when you leave it on, so since i am shutting mine off, i make a periodic donation to them instead...

---

### Post by grahammechanical on 2013-12-24
Do have an account on a social networking site? Use email? Use a mobile phone and text? Does the phone have GPS? You may be putting more information about yourself on somebody's servers then you will ever put into your installation of Ubuntu. Have you thought of that? 

There is a utility in Ubuntu called Security and Privacy. It allows me to decide if the OS should track my use of files and applications for the purpose of providing extra functionally. I can turn off online search for the Dash. I can opt in to have error reports sent to Canonical and to send occasional system information. They are both disabled by default. The search scopes that come with Unity 7, and there are many, can be individually turned off.

This is Canonical's privacy policy

[http://www.ubuntu.com/privacy-policy](http://www.ubuntu.com/privacy-policy)

For completeness here is the Fedora privacy policy and the Redhat privacy policy.

[https://fedoraproject.org/wiki/Legal:PrivacyPolicy?rd=FedoraProject:Privacy_policy](https://fedoraproject.org/wiki/Legal:PrivacyPolicy?rd=FedoraProject:Privacy_policy)

[http://www.redhat.com/footer/privacy-policy.html](http://www.redhat.com/footer/privacy-policy.html)

Regards.

---

### Post by junktext-0 on 2014-01-10
I am generally a fan of Ubuntu as I currently am using it to type this message, but not so much of their current "opt-out" policy towards the online Dash search feature.  I, too, worry about privacy issues and have turned off this capability.  My hope is that Canonical will one day make this an "opt-in" only feature.  I understand the points that there are already privacy concerns related to using web mail or social networking sites.  However, when one uses Facebook or Gmail they are essentially "opting-in" to allow them to use their data for analysis and for targeted advertising.  Why does this need to be a trend in a computer OS?  It doesn't as apparent in the vast number of other free and open Linux distros that do not conduct similar activities.

I also understand that Canonical needs revenue to function efficiently.  Why then do they not advertise their merchandise better?  I have bought a nice polo t-shirt, pens, and stickers willingly in the past.  Such actions does two things in one shot:  (1) Provides money to Canonical, and (2) advertises the Ubuntu brand by the very people who care to enlighten others still stuck on non-free operating systems.  Yet, my support may waiver of Ubuntu and may go back to Fedora if they persist with their "opt-out" policy of the online Dash results.  I know this feature is easy to disable, but I worry of supporting the trend of privacy erosion.  Why do you think that Richard Stallman called Ubuntu spyware?  He has a bit of a point.

And why do you think this issue will never die in the FOSS community?  To elaborate further, I hang out in the #ubuntu support channel on Freenode and I saw somebody bring up this very topic last night and was quite concerned as Fuji_in_Japan has mentioned in this thread.  This is because it basically goes against the principle of "openness" by 'hiding' the fact that your OS will be talking with third parties without your 'explicit' consent.  Meaning that those who are not that computer savvy will not even understand they are allowing their computer to spread their search details to the wind.

Lastly, why do you think Google and Facebook are constantly in the news about privacy concerns?  Because people and organizations become annoyed with their privacy policies and how they use/sell a person's data.  Does Canonical really want to jump on this bandwagon?  This simple attitude towards the online Dash feature has already caused a rift in the FOSS community (which is why we are even having this conversation).  Maybe Mr. Shuttleworth does deserve the Big Brother Award he won recently?  See this link if you don't know what I am talking about:  [http://news.slashdot.org/story/13/10/28/2210220/ubuntus-mark-shuttleworth-wins-austrias-big-brother-award](http://news.slashdot.org/story/13/10/28/2210220/ubuntus-mark-shuttleworth-wins-austrias-big-brother-award)  

Not to mention that the EFF seriously disapproves as well ([https://www.eff.org/deeplinks/2012/10/privacy-ubuntu-1210-amazon-ads-and-data-leaks](https://www.eff.org/deeplinks/2012/10/privacy-ubuntu-1210-amazon-ads-and-data-leaks)).  So, it's not just a few users here and there that are already annoyed.  Long live Ubuntu?  I guess we'll see.

---

### Post by thnewguy on 2014-01-12
I think saying no personal information is exposed is a bit of an over generalization. As I understand it, information sent to Canonical is anonimized before it is forwarded to third-parties. However, since the Dash/scopes talk to the third-parties directly to download images, it is trivial for them to link your searches with your IP address. The early versions of the Dash search feature did not use secure connections to download images either so people sniffing your network traffic could guess what your local searches were. Not sure if Canonical switched to secure connections with the latest release or not.

Anyway, your search information and IP address do leak out with the Dash, so yes, I would say there is a privacy concern when it comes to using Ubuntu until you turn off the search feature. As others have pointed out, it is fairly easy to disable the search function in the Settings panel, which removes the issue.

---

