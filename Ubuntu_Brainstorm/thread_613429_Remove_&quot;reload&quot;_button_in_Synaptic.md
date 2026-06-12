---
title: "Remove &quot;reload&quot; button in Synaptic"
date: 2007-11-14
forum: Ubuntu Brainstorm
---

### Post by sicofante on 2007-11-14
The reload button is meant to do something the software should do by itself: detect when repositories have changed or have been outdated (am I missing something else?)

I'm not asking to just remove the button and put the function somewhere else, but making Synaptic better from a usability point of view by being a bit more clever.

---

### Post by teasum on 2007-11-14
If I understand you correctly, I agree.  It seems that after I upgraded to Feisty, I started to get error messages when running my updates that stated I was attempting to install packages that were "NOT AUTHENTICATED."  I later figured out that this was because I had not updated (or 'reloaded'), via either apt-get, aptitude, or synaptic.  If you're suggesting that the package manager (either synaptic or update-manager) reload/update automatically, then I wholeheartedly agree.  If some of the more technically inclined forum surfers out there can explain this issue better than I, I'd be interested to hear about it.

---

### Post by smartboyathome on 2007-11-15
Don't get rid of the reload button. It may make it "look" smarter, but for those on slow or low bandwidth internet connections, it would make using synaptic a nightmare.

---

### Post by sicofante on 2007-11-15
> **smartboyathome said:**
> Don't get rid of the reload button. It may make it "look" smarter, but for those on slow or low bandwidth internet connections, it would make using synaptic a nightmare.
I don't quite get that. If you want it to update the repositories, you will need the bandwidth anyway. How does it make it better having to click on "reload" manually?

---

### Post by uboobtu on 2007-11-15
Yes, but you something you may not be aware of is this:  if I am in the process of selecting packages to download and install, and decide that I need to use my dialup connection to do something else, what happens when, because I finish selecting the packages, Synaptic automatically starts downloading them?  Not good.

---

### Post by sicofante on 2007-11-15
> **uboobtu said:**
> Yes, but you something you may not be aware of is this:  if I am in the process of selecting packages to download and install, and decide that I need to use my dialup connection to do something else, what happens when, because I finish selecting the packages, Synaptic automatically starts downloading them?  Not good.
I may have missed something but the reload button has nothing to do with starting downloads of currently selected packages.

---

### Post by smartboyathome on 2007-11-15
> **sicofante said:**
> I don't quite get that. If you want it to update the repositories, you will need the bandwidth anyway. How does it make it better having to click on "reload" manually?

Yes, but it would need to download the stuff over and over again to check if there are changes. This could cost much bandwidth and would make the connection painfully slow.

---

### Post by sicofante on 2007-11-15
> **smartboyathome said:**
> Yes, but it would need to download the stuff over and over again to check if there are changes. This could cost much bandwidth and would make the connection painfully slow.
I still don't follow, honestly. Why would Synatpic need to "download the stuff over and over again"? Maybe you would like an "offline-mode" for Synaptic (for removing software maybe?). That's OK with me but has little to do with the reload button functionality.

What I'm saying is: when you add or change a repository you're asked to "reload", you are asked to click on a button, when the software can do this pretty well for you and that's what it should do. If Synaptic needs to update its package listings, it should do when it launches too. No need for a "reload" button. If you need to work with Synaptic offline then maybe Synaptic should check first if you're online and ask you to connect when it needs too. Still no use for the reload button.

---

### Post by qamelian on 2007-11-15
> **sicofante said:**
> I still don't follow, honestly. Why would Synatpic need to "download the stuff over and over again"? Maybe you would like an "offline-mode" for Synaptic (for removing software maybe?). That's OK with me but has little to do with the reload button functionality.

What I'm saying is: when you add or change a repository you're asked to "reload", you are asked to click on a button, when the software can do this pretty well for you and that's what it should do. If Synaptic needs to update its package listings, it should do when it launches too. No need for a "reload" button. If you need to work with Synaptic offline then maybe Synaptic should check first if you're online and ask you to connect when it needs too. Still no use for the reload button.

The point is that the reload does need to download something to refresh the package list. If you are on a slow dial-up connection, especially one which is metered (the more data you move, the more you pay), then it becomes extremely important that any billable usage of your internet connection occurs only when you want it to. For example, my broadband account comes with a limited dialup service as backup or for roaming in non-broadband areas. I am only allowed a certain usage limit per month before I start getting charged extra. When I am in a situation in which I need to use the dial-up service, I make sure that nothing is going to potentially going to rack up usage charges without me knowing it. I don't even want Evolution checking my email unless I ask it to. Sometimes I might bring up Synaptic for some reason other than to actually install something. If I'm on my metered account, the last thing I want is for Synaptic to be running out and doing things which might result in extra billing for me. 

You might not think it would amount to much, but I found I could save myself $10-$12 dollars per month by not letting anything burn bandwidth behind my back. Over the course of a year, that amounts to a reasonably pleasant night on the town!

---

### Post by sicofante on 2007-11-15
> **qamelian said:**
> The point is that the reload does need to download something to refresh the package list. If you are on a slow dial-up connection, especially one which is metered (the more data you move, the more you pay), then it becomes extremely important that any billable usage of your internet connection occurs only when you want it to. Then please by all means don't add repositories at a time you don't want Synaptic to connect to the internet. Couldn't be easier...

Would you ask Firefox to have a "loag page" button that you would have to click each time you click on a link? No, if you don't want Firefox to connect to the internet you either don't use it or stop the dialup software from completing the connection. An application supposed to work with the internet should try to do so and it's up to you to stop the connection software (WHICH IS NOT PART OF SYNAPTIC) to complete the connection if it's not the right time for you.

Please, this has absolutely nothing to do with a system connecting to the internet without your permission. If EVERY time you update your repositories the software asks you to hit a button then there's a design mistake that's pretty easy to correct and I'm just asking for that.

---

### Post by smartboyathome on 2007-11-15
> **sicofante said:**
> Then please by all means don't add repositories at a time you don't want Synaptic to connect to the internet. Couldn't be easier...

Would you ask Firefox to have a "loag page" button that you would have to click each time you click on a link? No, if you don't want Firefox to connect to the internet you either don't use it or stop the dialup software from completing the connection. An application supposed to work with the internet should try to do so and it's up to you to stop the connection software (WHICH IS NOT PART OF SYNAPTIC) to complete the connection if it's not the right time for you.

Please, this has absolutely nothing to do with a system connecting to the internet without your permission. If EVERY time you update your repositories the software asks you to hit a button then there's a design mistake that's pretty easy to correct and I'm just asking for that.

The answer to that problem shouldn't be "don't add repositories". Instead, it shouldn't do this in the first place.

Also, Firefox is DIFFERENT from Synaptic. What you are saying makes me think "Should there be a Send Mail button in Evolution? NO, because Evolution should try to guess when you are done sending the letter and send it for you, even though you may not be done!"). Anyway, your solution doesn't sound like the best solution to this problem to me.

EDIT: One more thing, the system checks for updates automatically once each day, so you shouldn't NEED to push "reload".

---

### Post by ssam on 2007-11-15
it should not need to redownload the whole package list to check for changes. i think apt already only downloads the package list if it has changed (it probably checks http headers).

if you open a terminal and run

```
sudo apt-get update
```

then second to last line printed shows how much it downloaded.

then run it again and see how much it gets. on my second run it claims to only have downloaded 7 bytes.

---

### Post by smartboyathome on 2007-11-15
Your right, but running it constantly (ie: it took <1s to download all 8b the second time), it would really add up after 5-10 minutes.

---

### Post by sicofante on 2007-11-15
> **smartboyathome said:**
> Also, Firefox is DIFFERENT from Synaptic. What you are saying makes me think "Should there be a Send Mail button in Evolution?
You can't be serious. Of course Firefox is different from Synaptic, but the act of Firefox connecting to the internet as a direct and exclusive consequence of you clicking on a link is identical and perfectly comparable. There are a number of actions you can take after you have written your e-mail ("send", "save" or "delete" are just three that bump into my mind, let alone only you decide when you're done editing it). There's only one course of action once you decide you will add repositories in Synaptic: click the reload button. In fact, you get a big dialog bog saying exactly that "Please click the reload button". I'm saying: "Would you Synaptic be nice and logical and click it for me since there's nothing else anyone in his right mind would want as yourself are perfectly implying with your big obvious screaming dialog box. Thanks?"

Maybe you can illustrate another use of the reload button I have missed. Or you might show me why you would want to alter the repositories list WITHOUT having the package list updated. I'm honestly wondering.

I'm trying to understand your point. Maybe you're saying you want to edit your repositories list and leave updating for later?

> **smartboyathome said:**
> Your right, but running it constantly (ie: it took <1s to download all 8b the second time), it would really add up after 5-10 minutes.
Why on God's green Earth would you want to run it constantly???

---

### Post by qamelian on 2007-11-15
> **sicofante said:**
> Then please by all means don't add repositories at a time you don't want Synaptic to connect to the internet. Couldn't be easier...

Would you ask Firefox to have a "loag page" button that you would have to click each time you click on a link? No, if you don't want Firefox to connect to the internet you either don't use it or stop the dialup software from completing the connection. An application supposed to work with the internet should try to do so and it's up to you to stop the connection software (WHICH IS NOT PART OF SYNAPTIC) to complete the connection if it's not the right time for you.

Please, this has absolutely nothing to do with a system connecting to the internet without your permission. If EVERY time you update your repositories the software asks you to hit a button then there's a design mistake that's pretty easy to correct and I'm just asking for that.

No, I wouldn't ask Firefox to have a load page button, but neither would I used a feature that caused pages to refresh automatically. And just because I chose to add a new repo at a particular time does not mean I intend to use it right that moment. And it has everything to do with my system connecting to the internet without my permission. It's not my fault if you can't understand why someone might prefer things the way they are. In my opinion, the change you want made would be a design flaw, not the other way around. 

Just because an app is meant to work with the internet does not by any stretch of the imagination mean that it should do so persistently. Why do you think email clients allow you to set an interval for checking for messages instead of constantly polling the email server for updates. Simple. Because this kind of behaviour is not always desirable. 

Frankly, if your idea were implemented, I would stop using Synaptic entirely.

---

### Post by smartboyathome on 2007-11-16
> **sicofante said:**
> Why on God's green Earth would you want to run it constantly???

What you are saying is it should be "smart" and update your list automatically, this can only happen if it downloads the lists automatically. And constantly downloading the list is a waste of bandwidth (unless you have a solution which doesn't use bandwidth).

Also, what I meant about Firefox and Synaptic are that even the functionality is different. What you are comparing it to should be more compared to automatically reloading on every page you visit in firefox (and we all know that is a huge waste of bandwidth). Clicking a link in Firefox would be more like double clicking on a package in Synaptic and it being installed, no questions asked (which I do not like either).

---

### Post by sicofante on 2007-11-16
> **qamelian said:**
> No, I wouldn't ask Firefox to have a load page button, but neither would I used a feature that caused pages to refresh automatically.

> **smartboyathome said:**
> constantly downloading the list is a waste of bandwidth
Unless I'm missing something, you guys seem to have a fixation with "constant updating", which no one does to my knowledge. But anyway, let's stop the discussion here and let me rephrase my proposal:

Put an option in Synaptic preferences so that after modifying the repos list the software won't ask the user to manually click on the reload button but will do it automatically instead. Users on flat rate high bandwidth connections will appreciate that logical step being taken by the software. Users on low bandwidth dialup or otherwise loving to do things manually will be able to click on the reload button by themselves when they feel like.

Better?

---

### Post by rsambuca on 2007-11-16
> **sicofante said:**
> Then please by all means don't add repositories at a time you don't want Synaptic to connect to the internet. Couldn't be easier...


So now you want the Operating System to dictate to us, the humans, when and how we should use the system???

---

### Post by sicofante on 2007-11-16
> **rsambuca said:**
> So now you want the Operating System to dictate to us, the humans, when and how we should use the system???
Errr... yeah, sure.

---

### Post by qamelian on 2007-11-16
> **sicofante said:**
> Unless I'm missing something, you guys seem to have a fixation with "constant updating", which no one does to my knowledge. But anyway, let's stop the discussion here and let me rephrase my proposal:

Put an option in Synaptic preferences so that after modifying the repos list the software won't ask the user to manually click on the reload button but will do it automatically instead. Users on flat rate high bandwidth connections will appreciate that logical step being taken by the software. Users on low bandwidth dialup or otherwise loving to do things manually will be able to click on the reload button by themselves when they feel like.

Better?

Actually, yes. That would be a perfectly acceptable compromise, because it offers users the ability to choose the behaviour that best suits their needs.

You definitely are missing the point about why your original suggestion was objectionable. I don't expect you to understand why I might do something different than you, but you have no right to expect me to change my work habits (which are often set out of necessity, not choice) to match yours. My problem had nothing to do with "constant updating", so please don't put words in my mouth. That is nothing short of ignorant. My problem was with something happening automatically that potentially has a negative impact on me. In fact, I can easily think of a scenario in which I would add a an additional repo with no intentional of actually needing to use that repo until later, when I am back on my unmetered account. That being the case, why would I want it to update right away when it might cost me money for bandwidth usage.

It isn't rocket science.

---

### Post by smartboyathome on 2007-11-16
> **sicofante said:**
> Unless I'm missing something, you guys seem to have a fixation with "constant updating", which no one does to my knowledge. But anyway, let's stop the discussion here and let me rephrase my proposal:

Put an option in Synaptic preferences so that after modifying the repos list the software won't ask the user to manually click on the reload button but will do it automatically instead. Users on flat rate high bandwidth connections will appreciate that logical step being taken by the software. Users on low bandwidth dialup or otherwise loving to do things manually will be able to click on the reload button by themselves when they feel like.

Better?

Better. Perhaps you can write up a spec about this on launchpad. It would take a little coding, but it can be done (it would have to be an "Automatically refresh every X seconds/minutes/hours/etc). :)

---

### Post by 23meg on 2007-11-16
No need for a spec; filing a bug that indicates that the behaviour after modifying repositories should change would be more appropriate.

---

### Post by Meomix on 2007-11-16
i agree i find it troublesome to always click the bloody **Reload** when im fetching for programs what if i forget to click the button and my download ends up going down the toilet?
auto-reload should have been invented *longg* ago.

---

### Post by altonbr on 2007-11-16
While were at it, how about merging software source with Synaptic since they both reload the repositories. No need for so many tiny apps. Merge them all!

---

### Post by sicofante on 2007-11-16
> **qamelian said:**
> I don't expect you to understand why...
Great then.

> **smartboyathome said:**
> "Automatically refresh every X seconds/minutes/hours/etc). :)
No, just update automatically after modifying the repositories list.

> **23meg said:**
> No need for a spec; filing a bug that indicates that the behaviour after modifying repositories should change would be more appropriate.
Thanks for the tip. I'll do that ASAP.

EDIT: As a matter of fact, there was already a suggestion like this in Launchpad here: [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/94152](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/94152). I just added a comment and a link to this very thread.

> **Meomix said:**
> i agree i find it troublesome to always click the bloody **Reload** when im fetching for programs what if i forget to click the button and my download ends up going down the toilet?
auto-reload should have been invented *longg* ago.
Exactly. You got it exactly right.

Thanks for all the feedback.

---

### Post by smartboyathome on 2007-11-17
> **sicofante said:**
> No, just update automatically after modifying the repositories list.

Ok, then. Don't remove the reload button then, as you need to refresh the package list even when you don't add/delete repositories.

---

### Post by sicofante on 2007-11-17
> **smartboyathome said:**
> Ok, then. Don't remove the reload button then, as you need to refresh the package list even when you don't add/delete repositories.
Sorry, now I got you and your need for "constant updates". My mistake. However, as you pointed out earlier, the system updates the list once a day, so refreshing might not deserve it's own button.

Anyway, the proposal as it is in Launchpad now is perfectly fine for me.

---

### Post by rsambuca on 2007-11-17
> **sicofante said:**
> Sorry, now I got you and your need for "constant updates". My mistake. However, as you pointed out earlier, the system updates the list once a day, so refreshing might not deserve it's own button.

Anyway, the proposal as it is in Launchpad now is perfectly fine for me.

It doesn't necessarily refresh every day.  It depends on your settings.  You can have it set to weekly or even every two weeks.

---

