---
title: "What's with all this cookie awareness?"
date: 2012-07-10
forum: The Cafe
---

### Post by t0p on 2012-07-10
Cookies have been used by websites for ages.  But just recently a bunch of sites have started telling us about them, for instance having a banner on the home page that says 
> This site uses cookies. By continuing to browse the site you are agreeing to our use of cookies.

If you go to [this Google results page]("https://encrypted.google.com/search?client=ubuntu&channel=fs&q=%22this+site+uses+cookies%22&ie=utf-8&oe=utf-8&gl=uk"), you'll see it is a growing phenomenon.  So why's this come about?  Was there a big Cookies v Privacy court case recently that I don't know about?

---

### Post by fatality_uk on 2012-07-10
> **t0p said:**
> Cookies have been used by websites for ages.  But just recently a bunch of sites have started telling us about them, for instance having a banner on the home page that says 


If you go to [this Google results page]("https://encrypted.google.com/search?client=ubuntu&channel=fs&q=%22this+site+uses+cookies%22&ie=utf-8&oe=utf-8&gl=uk"), you'll see it is a growing phenomenon.  So why's this come about?  Was there a big Cookies v Privacy court case recently that I don't know about?

The EU has deemed (rightly so imho) that people need to be made aware that sites they visit store data about them.

[http://www.ico.gov.uk/for_organisations/privacy_and_electronic_communications/the_guide/cookies.aspx](http://www.ico.gov.uk/for_organisations/privacy_and_electronic_communications/the_guide/cookies.aspx)

---

### Post by Dry Lips on 2012-07-10
Well, sites that are hosted in the EU now have to comply with the new European cookie directive which went into effect in May.

[http://eucookiedirective.com/](http://eucookiedirective.com/)

---

### Post by wilee-nilee on 2012-07-10
Intrinsically I would say some of us want no cookies saved and a limitation on the ones used when browsing, for personal reasons, I'm in this camp myself.

---

### Post by Primefalcon on 2012-07-10
overactive paranoia tbh.... only data that has already been gathered by other means can be stored in a cookie.... and unlss you want a stateless web... no logins or such.... get over it since thats what most sites use cookies for... remembering who you are so when you login or change site prefs the site can remember that you said to do that....

---

### Post by fatality_uk on 2012-07-10
> **Primefalcon said:**
> overactive paranoia tbh.... only data that has already been gathered by other means can be stored in a cookie.... and unlss you want a stateless web... no logins or such.... get over it since thats what most sites use cookies for... remembering who you are so when you login or change site prefs the site can remember that you said to do that....

"overactive paranoia tbh" until you understand what data can and is being used by ad merchants for instance. They can and do track and profile you in real time across multiple domains.

---

### Post by SeijiSensei on 2012-07-10
Unfortunately it's probably impossible to explain to ordinary people the difference between a session cookie, which has a short lifespan and is deleted when the browser is closed, and a persistent cookie which has a long expiration.

I use session cookies on nearly every site I build to manage authentication and track users during a browsing session.  I never leave persistent cookies behind because I don't need them and because they represent a privacy issue.

If you use Firefox, I strongly recommend using the [Ghostery]("http://www.ghostery.com/") add-on which lets you block persistent cookies from advertising sites.  On most commercial sites I visit, Ghostery will have blocked half-a-dozen or more cookies from sites that track your browsing behavior.  Occasionally you'll find a site doesn't work unless a specific cookie is permitted.  I find this to be especially true on sites with video, where the video won't play unless the site can set a cookie.  You can either disable Ghostery temporarily or use trial-and-error to find the minimal number of cookies required to make the site work then whitelist them.

---

### Post by Primefalcon on 2012-07-10
meh, web sites should switch over to evercookies as session cookies.... apparently a lot of sites such as hulu, aol, spotify  and such are already using them anyhow.... good luck deleting those easily.... then again there's always nevercookie

---

### Post by CharlesA on 2012-07-10
> **Primefalcon said:**
> meh, web sites should switch over to evercookies as session cookies.... apparently a lot of sites such as hulu, aol, spotify  and such are already using them anyhow.... good luck deleting those easily.... then again there's always nevercookie
Those are flash cookies, yeah? I checked Firefox and it has the option to clear flash cookies from the "Clear recent history" dialog box.

---

### Post by Primefalcon on 2012-07-10
> **CharlesA said:**
> Those are flash cookies, yeah? I checked Firefox and it has the option to clear flash cookies from the "Clear recent history" dialog box.
they arn't just flash cookies.... and ever cookies sets normal cookies, flash cookies, cache cookies, local storage cookies amongst others in different locations....

even if just one of these are left, it'll repopulate every single one of them... they are very very hard to get rid of

actually here;s alist of the place it stores id

> 

    Standard HTTP cookies
    Local Shared Objects (Flash cookies)
    Silverlight Isolated Storage
    Storing cookies in RGB values of auto-generated, force-cached PNGs using HTML5 Canvas tag to read pixels (cookies) back out
    Storing cookies in Web history
    Storing cookies in HTTP ETags
    Storing cookies in Web cache
    window.name caching
    Internet Explorer userData storage
    HTML5 Session Storage
    HTML5 Local Storage
    HTML5 Global Storage
    HTML5 Database Storage via SQLite

The developer is looking to add the following features:

    Caching in HTTP Authentication
    Using Java to produce a unique key based on NIC information.

btw check out the guys site: [http://samy.pl/](http://samy.pl/)

it is very cool.....

---

### Post by CharlesA on 2012-07-11
Wow, that sounds quite nasty.

---

### Post by Primefalcon on 2012-07-11
> **CharlesA said:**
> Wow, that sounds quite nasty.
just makes persistent cookies.... persistent not really as big of a deal as it sounds.... theres a firefox plugin called nevercookie to handle them too.... also been around for a few years now, and the big sites I mentioned are using them.

---

### Post by robtygart on 2012-07-11
I do not like Cookies. I use Cookie Whielist, along with Ghostery and Betterprivacy.

---

### Post by Primefalcon on 2012-07-11
> **robtygart said:**
> I do not like Cookies. I use Cookie Whielist, along with Ghostery and Betterprivacy.
better look into nevercookie then too..

you know without cookies and other ways to remember you, every single page would be individual,  so there'd be no logging into sites, no forums such as this one your posting to or much else on the web right

---

### Post by SeijiSensei on 2012-07-11
When even well-informed people like robtygart make blanket references to "cookies," it reinforces the point I made earlier about session vs. persistent cookies.

We've now reached the point where the public perception of "cookies" is that they are all pernicious, having no other purpose than to let advertisers track our every move across the Internet.  In reality, many cookies, particularly session cookies, make it possible to build web applications despite the "stateless" nature of the HTTP protocol itself.  

Now it's certainly possible to build effective sites without cookies.  All my sites use session cookies if the browser makes that option available, but for people who block cookies I revert to putting the session ID in the site URL.  I have some custom PHP functions that test whether the browser accepts cookies.  When I include a within-site link, I write the site's URL by calling a function that either adds the session ID to the link's URL or relies on the browser's cookie to provide the ID.  It is thus possible to honor a person's choice not to accept browser cookies and still build functioning sites.  

Having the session ID in the URL itself can be problematic if someone bookmarks the page with the ID included in the URL.  I have to include additional code to determine that the ID provided in the bookmarked link is stale and restart the session with a new one.  Search spiders pose the same problem since they always operate in a cookie-free manner. 

As a web user, I find cookies too valuable to block them entirely in my browser.  I let add-ons like Ghostery handle that problem for me.

---

### Post by sffvba[e0rt on 2012-07-11
Reading this thread I couldn't help but think of [this]("http://youtu.be/-qTIGg3I5y8").


404

---

### Post by robtygart on 2012-07-11
> **Primefalcon said:**
> better look into nevercookie then too..

you know without cookies and other ways to remember you, every single page would be individual,  so there'd be no logging into sites, no forums such as this one your posting to or much else on the web right

Its not about blocking them all, I just want to be able to delete them and block them for those sites that I don't care about. Some sites I just want the content, I don't need or want to be apart of it.

If I knew how to only block the tracking cookies I would.

---

### Post by pqwoerituytrueiwoq on 2012-07-11
[IMG]http://i.imgur.com/m7S3a.png[/IMG]
you will need to add exceptions for some cookies (eg putlocker)
i only have 3 exceptions and one was for my google toobar back when i used it the another is used with a greasemoenky script i use to access a site without being on it all the time

---

### Post by KiwiNZ on 2012-07-11
I have more important things to worry about.

---

### Post by Primefalcon on 2012-07-12
> **KiwiNZ said:**
> I have more important things to worry about.
to you maybe... different people have different priorities.... personally I am not all that worried about it either tbh..... 

and peple breaking cookies to me as a web developer is to be honest an annoyance....

for utter privacy though if you really need it.... download the tor browser

[https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en)

you will be untraceable.....

---

### Post by CharlesA on 2012-07-12
Nothing is ever "untraceable" on the internet. There will always be some record, somewhere.

As for my website, I try not to use cookies, but that makes things such as CSS switchers and whatnot difficult.

---

### Post by SeijiSensei on 2012-07-12
I use this function to rewrite all within-site URLs.  It defaults to using cookies if available, otherwise it appends the session ID to the GET request:

```

class sessions {
    var $sess_name='mysession';

    function self_url($string="") {
                          
        $sesstext="";
        if (!isset($_COOKIE[$this->sess_name])) {
            $sesstext="&".$this->sess_name."=".session_id();
        }   

        # remove any extraneous delimiters
        # starts with "?" or "&"
        if (substr($string,0,1)=="?" || substr($string,0,1)=="&") {
            $string=substr($string,1);
        }
        # ends with "&"
        if (substr($string,-1,1)=="&") {
            $string=substr($string,0,-1);
        }

        $self_url=$_SERVER["PHP_SELF"]."?".$string.$sesstext;

        return $self_url;

    }

[other stuff]
}

```

I've used this for years with nary a problem.  In the href field, I just use 

```

$s=new sessions;

echo '<a href="'.$s->self_url('[URL parameters]').'">linktext</a>';


```

---

### Post by CharlesA on 2012-07-12
Nice workaround Seiji!

I was thinking of using PHP sessions, but I never actually got around to writing up a secondary CSS for my site.

---

### Post by Primefalcon on 2012-07-12
> **CharlesA said:**
> Nothing is ever "untraceable" on the internet. There will always be some record, somewhere.

As for my website, I try not to use cookies, but that makes things such as CSS switchers and whatnot difficult.
maybe not 100% since there's always a possibility of a vulnerability... and then they go through the possible crack each step in the onion process.... using brute force to decrypt each step.. which would take how long.... 200, 300 years or more...... this is even assuming they have access to all the servers some of hich will be located overseas which they simply dont have access to....


but when the feds are unable to trace back people (people they really want are trying to even pass laws to ban encryption) that are using tor to access silk road or to even trace where the site is itself at all since its using an onion domain.... I'd say its safe to say your anonymous

---

### Post by Grenage on 2012-07-12
If you're on the internet, you're not anonymous to the authorities.  Of course, if 'the authorities' is the authorities of various countries, you'd have to really, really be worth their time.  It's fair to say that's nobody here!

It's a lot easier to just jack someone's connection and keep moving.

---

### Post by Primefalcon on 2012-07-12
> **Grenage said:**
> If you're on the internet, you're not anonymous to the authorities.  Of course, if 'the authorities' is the authorities of various countries, you'd have to really, really be worth their time.  It's fair to say that's nobody here!

It's a lot easier to just jack someone's connection and keep moving.
whether or not you personally are known to the authorities is not of relevance, it's whether they know what sites your visiting or not.... or whether they can trace you back from a site.... the realistic answer is no...

If otherwise a major drug dealing website like silk bay wouldn't still be in operation....

---

### Post by Grenage on 2012-07-12
My point was, the realistic answer is an almighty 'yes'; it's just not worth their time.

---

### Post by Primefalcon on 2012-07-12
> **Grenage said:**
> My point was, the realistic answer is an almighty 'yes'; it's just not worth their time.
to what? sieze tor servers in over a dozen different countries, forget the fact most of those computers are probably not keeping logs, which if even 1 isn't they'd be sol since each step of the tor process encrypts

---

### Post by robtygart on 2012-07-12
Well even with all cookies blocked your ISP provider still knows were you have been correct? So if the authorities want to find out were you have been they will just contact them. 

If you want to avoid the authorities, Tor would be great along with borrowing someones wifi across town. 

My big annoyance is, what I do online is my business and I don't want big corporations knowing what I do. 

Although a lot of websites make money on adds and I think its important to support them, I don't want sites like "Facebook" tracking me across the web, after I click off that site I think the tracking should stop there.

---

### Post by Primefalcon on 2012-07-12
> **robtygart said:**
> Well even with all cookies blocked your ISP provider still knows were you have been correct? So if the authorities want to find out were you have been they will just contact them. 

If you want to avoid the authorities, Tor would be great along with borrowing someones wifi across town. 

My big annoyance is, what I do online is my business and I don't want big corporations knowing what I do. 

Although a lot of websites make money on adds and I think its important to support them, I don't want sites like "Facebook" tracking me across the web, after I click off that site I think the tracking should stop there.
thats one reason I like the tor browser it drops cookies and such after each session... the bad site of that is it wont remember your login details and such and because o all the encryption and random routing its somewhat slower on page loads (its not too terrible though)

---

### Post by KiwiNZ on 2012-07-12
Does one map every CCTV camera or speed camera/ reg plate camera in order to avoid them. Never use an ATM, EFTPOS terminal. Never fly or use a passport. Never use a Security access card. 

One is tracked in all aspects of life teat it with a giant who cares and that is a lot removed from ones worry list.

Personally I don't give a toss.

---

### Post by robtygart on 2012-07-12
> thats one reason I like the tor browser it drops cookies and such after each session... the bad site of that is it wont remember your login details and such and because o all the encryption and random routing its somewhat slower on page loads (its not too terrible though) 

From what I have read, If you want to remain anonymous then you should not login to anything personally identifying.  

> **KiwiNZ said:**
> Does one map every CCTV camera or speed camera/ reg plate camera in order to avoid them. Never use an ATM, EFTPOS terminal. Never fly or use a passport. Never use a Security access card. 

One is tracked in all aspects of life teat it with a giant who cares and that is a lot removed from ones worry list.

Personally I don't give a toss.

The US is now going to use drones to watch you. So those CCTV cameras are nothing to worry about.

---

### Post by David Andersson on 2012-07-12
(Off topic)

> **KiwiNZ said:**
> Does one map every CCTV camera or speed camera/ reg plate camera in order to avoid them. Never use an ATM, EFTPOS terminal. Never fly or use a passport. Never use a Security access card. 


I do. Except the CCTV cameras, that I don't know how to avoid.

Cash is King. In my country, you can still travel by train without revealing your social security number or credit card number. But I suspect, within a few years not even that will be possible.

---

### Post by tjeremiah on 2012-07-12
> **robtygart said:**
> From what I have read, If you want to remain anonymous then you should not login to anything personally identifying.  



The US is now going to use drones to watch you. So those CCTV cameras are nothing to worry about.

yeah I read this the other day. Some truly scary stuff. What if they get hacked and start flying like a chicken without its head :confused:

---

### Post by Primefalcon on 2012-07-12
> **tjeremiah said:**
> yeah I read this the other day. Some truly scary stuff. What if they get hacked and start flying like a chicken without its head :confused:
Just wait until law is passed that every must have a chip inserted... not too far from that now tbh... then they'll probably want to hook that chip up to your eyeballs and ears some years after that.. privacy is something that I don't think will last

---

### Post by robtygart on 2012-07-12
> **tjeremiah said:**
> yeah I read this the other day. Some truly scary stuff. What if they get hacked and start flying like a chicken without its head :confused:

They already have been hacked. 

Search for "Texas college hacks drone in front of DHS"

**Sorry this is very off topic :oops:**




Wanting more privacy is one big reason why I switched to Linux .

---

### Post by nec207 on 2012-07-12
> **SeijiSensei said:**
> Unfortunately it's probably impossible to explain to ordinary people the difference between a session cookie, which has a short lifespan and is deleted when the browser is closed, and a persistent cookie which has a long expiration.
 
I use session cookies on nearly every site I build to manage authentication and track users during a browsing session. I never leave persistent cookies behind because I don't need them and because they represent a privacy issue.
 
If you use Firefox, I strongly recommend using the [Ghostery]("http://www.ghostery.com/") add-on which lets you block persistent cookies from advertising sites. On most commercial sites I visit, Ghostery will have blocked half-a-dozen or more cookies from sites that track your browsing behavior. Occasionally you'll find a site doesn't work unless a specific cookie is permitted. I find this to be especially true on sites with video, where the video won't play unless the site can set a cookie. You can either disable Ghostery temporarily or use trial-and-error to find the minimal number of cookies required to make the site work then whitelist them.
 
That has to do wih google and yahoo using cookies to make profile of your browsing habit and than give you adds on that . And many people hate web sites that do that and more so big companies.
 
Go to ebay or amazon again base on your browsing habit you going get adds and same with youtube type in games like Doom 3 and Quake and next youtube going to be giving you recommended videos on Doom 3 and Quake.

---

