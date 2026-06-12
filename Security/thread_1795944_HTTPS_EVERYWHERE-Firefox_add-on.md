---
title: "HTTPS EVERYWHERE-Firefox add-on"
date: 2011-07-03
forum: Security
---

### Post by amahi on 2011-07-03
[COLOR=Blue]
HTTPS Everywhere[/COLOR] 

is a Firefox add-on produced as a collaboration between The Tor Project
([https://www.torproject.org](https://www.torproject.org)) and the Electronic Frontier Foundation ([https://eff.org/](https://eff.org/)). It encrypts
your communications with a number of major Web sites, including Google, Wikipedia, and popular
social networking platforms such as Facebook and Twitter.
Many sites on the Web offer some support for encryption over HTTPS, but make it difficult to
use. For instance, they may connect you to HTTP by default, even when HTTPS is available. Or
they may fill encrypted pages with links that go back to the unencrypted site. This way, data
(such as usernames and passwords) sent to and received by these Web sites are transferred as
plain text and are easy to read by third parties.
The HTTPS Everywhere extension fixes these problems by rewriting all requests to these sites
to HTTPS. (Although the extension is called "HTTPS Everywhere", it only activates HTTPS on a
particular list of sites and can only use HTTPS on sites that have chosen to support it. It cannot
make your connection to a site secure if that site does not offer HTTPS as an option.)
Please note that some of those sites still include a lot of content, such as images or icons, from
third party domains that is not available over HTTPS. As always, if the browser's lock icon is
broken or carries an exclamation mark, you may remain vulnerable to some adversaries that
use active attacks or traffic analysis. However, the effort required to monitor your browsing
should still be usefully increased.
Some Web sites (such as Gmail) provide HTTPS support automatically, but using HTTPS
Everywhere will also protect you from SSL-stripping attacks, in which an attacker hides the
HTTPS version of the site from your computer if you initially try to access the HTTP version.
Additional information can be found at: [https://www.eff.org/https-everywhere](https://www.eff.org/https-everywhere).


[COLOR=Blue]NSTALLATION[/COLOR]

First, download the HTTPS Everywhere extension from the official Web site:
[COLOR=DarkOrange]https://www.eff.org/https-everywhere[/COLOR]
Select the newest release. 

[COLOR=Blue]CONFIGURATION[/COLOR]:
firefox>tools>add-ons
[IMG]http://setp113.persiangig.com/https-everywhere1.png[/IMG]

To access the HTTPS Everywhere settings panel in Firefox 4 (Linux), click on the Firefox menu at
the top left on your screen and then select Add-ons Manager. (Note that in different versions of
Firefox and different operating systems, the Add-ons Manager may be located in different places
in the interface.)

[COLOR=Blue]USAGE[/COLOR]

Once enabled and configured, HTTPS Everywhere is very easy and transparent to use. Type an
insecure HTTP URL (for example, [COLOR=Red]http://www.google.com[/COLOR]).
Press Enter. You will be automatically redirected to the secure HTTPS encrypted Web site (in this
example: [COLOR=SeaGreen]https://encrypted.google.com[/COLOR]). No other action is needed.

[COLOR=RoyalBlue]Adding support for additional sites in HTTPS Everywhere[/COLOR]

You can add your own rules to the HTTPS Everywhere add-on for your favorite Web sites. You
can find out how to do that at: [https://www.eff.org/https-everywhere/rulesets](https://www.eff.org/https-everywhere/rulesets). The benefit of
adding rules is that they teach HTTPS Everywhere how to ensure that your access to these sites
is secure. But remember: HTTPS Everywhere does not allow you to access sites securely unless
the site operators have already chosen to make their sites available through HTTPS. If a site
does not support HTTPS, there is no benefit to adding a ruleset for it.
If you are managing a Web site and have made an HTTPS version of the site available, a good
practice would be to submit your Web site to the official HTTPS Everywhere release.

[ *Have a Good Time*]("https://encrypted.google.com/url?sa=t&source=web&cd=2&ved=0CCgQtwIwAQ&url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DOwPLeczyhKg&rct=j&q=have%20good%20time&ei=DGMQTq-hMcKWOvGWtbYL&usg=AFQjCNGTwPfUBddMpagnBsHxH0W7XhvW2w&cad=rja")

---

