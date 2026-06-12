---
title: "Portable Tor?"
date: 2010-06-15
forum: Security
---

### Post by PDA1 on 2010-06-15
I've tried to create Portable Tor to run on a flash drive but have no success.  

Whenever I try to extract the file- tor-browser-gnu-linux-i686-1.0.7-dev-en-US(2).tar.gz to the USB flash drive the extraction process almost ends but I get the error messages as follows;

```
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/content/editpl.xul: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/content/progress.xul: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/content/extovl.xul: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/content/bpopt.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/content/bp.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/content/logo.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/content/pie.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/content/bp.xul: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/content/bphelp.html: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/content/LICENSE: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/content/BetterPrivacy.html: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/content/sanitizer.xul: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/content/menu.xul: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/content: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome.manifest: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/preferences.xul: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/preferences.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/code/HTTPS.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/code/HTTPSRules.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/code/IOUtil.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/code/STS.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/code/Cookie.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/code/tags: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/code/Thread.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/code: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/rules/Twitter.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/rules/Wikipedia.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/rules/Ixquick.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/rules/Facebook.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/rules/NYTimes.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/rules/Google.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/rules/WashingtonPost.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/rules/EFF.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content/rules: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/content: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/skin/https-everywhere.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/skin/https-everywhere.xcf: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/skin: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/locale/en/https-everywhere.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/locale/en: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome/locale: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/chrome: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/components/svn-commit.tmp: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/components/https-everywhere.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/components: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/install.rdf: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org/LICENSE.txt: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/https-everywhere@eff.org: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/chrome.manifest: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/install.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/NoScript_License.txt: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/chrome.manifest: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/.autoreg: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/chrome/noscript.jar: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/chrome: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/mozilla.cfg: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/META-INF/zigbert.sf: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/META-INF/zigbert.rsa: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/META-INF/manifest.mf: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/META-INF: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/components/noscriptService.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/components: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/install.rdf: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/GPL.txt: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/defaults/preferences/noscript.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/defaults/preferences: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}/defaults: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{73a6fe31-595d-460b-a920-fcc0f8843232}: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/skin/BetterPrivacyButton.css: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/skin/btn_small.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/skin/btn_large.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/skin: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/install.rdf: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/fr/bp.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/fr/bp.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/fr: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/en-US/bp.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/en-US/bp.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/en-US: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/tr-TR/bp.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/tr-TR/bp.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/tr-TR: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/da-DK/bp.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/da-DK/bp.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/da-DK: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/es-AR/bp.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/es-AR/bp.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/es-AR: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/zh-TW/bp.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/zh-TW/bp.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/zh-TW: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/pt-BR/bp.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/pt-BR/bp.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/pt-BR: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/de-DE/bp.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/de-DE/bp.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/de-DE: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/vi/bp.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/vi/bp.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/vi: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/nl/bp.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/nl/bp.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/nl: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/zh-CN/bp.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/zh-CN/bp.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale/zh-CN: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/locale: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome.manifest: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/content/preferences.xul: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/content/preferences.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/content/popup.xul: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/content/torbutton.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/content/pref-connection-info.xul: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/content/torbutton.xul: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/content/jshooks.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/content/torbutton_util.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/content/pref-connection.xul: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/content/about.xul: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/content/contents.rdf: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/content/torbutton_tb.xul: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/content: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/skin/tor-enabled-24.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/skin/tor-disabled-16.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/skin/p.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/skin/tor-enabled-16.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/skin/tor-24.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/skin/tor-16.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/skin/tor-disabled-24.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/skin/poff.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/skin/tor.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/skin/torbutton.css: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/skin/punknown.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/skin/contents.rdf: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/skin: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/gl/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/gl/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/gl: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/es/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/es/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/es: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/eu/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/eu/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/eu: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/nb/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/nb/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/nb: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/fr/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/fr/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/fr: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/sq/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/sq/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/sq: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/sw/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/sw/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/sw: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ro/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ro/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ro: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/is/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/is/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/is: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/bms/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/bms/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/bms: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/hr/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/hr/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/hr: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/en/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/en/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/en: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/mt/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/mt/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/mt: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/it/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/it/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/it: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/fi/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/fi/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/fi: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/pa/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/pa/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/pa: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/pt/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/pt/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/pt: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ja/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ja/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ja: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ca/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ca/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ca: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ru/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ru/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ru: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/hi/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/hi/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/hi: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/zh-HK/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/zh-HK/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/zh-HK: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/af/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/af/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/af: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/sv/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/sv/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/sv: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/gu/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/gu/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/gu: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/el/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/el/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/el: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/km/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/km/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/km: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/fur/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/fur/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/fur: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ko/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ko/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ko: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/cs/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/cs/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/cs: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/zh-TW/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/zh-TW/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/zh-TW: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/bg/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/bg/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/bg: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/pt-BR/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/pt-BR/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/pt-BR: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ku/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ku/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ku: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ar/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ar/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ar: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/he/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/he/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/he: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/sl/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/sl/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/sl: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/th/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/th/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/th: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/tr/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/tr/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/tr: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ka/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ka/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/ka: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/fa/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/fa/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/fa: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/da/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/da/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/da: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/bo/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/bo/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/bo: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/vi/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/vi/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/vi: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/de/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/de/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/de: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/id/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/id/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/id: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/nl/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/nl/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/nl: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/hu/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/hu/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/hu: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/pl/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/pl/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/pl: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/zh-CN/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/zh-CN/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/zh-CN: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/uk/torbutton.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/uk/torbutton.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale/uk: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome/locale: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome.manifest.jar: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/CREDITS: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/components/ignore-history.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/components/nsSessionStore36.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/components/nsSessionStore2.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/components/nsSessionStore3.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/components/block-livemarks.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/components/crash-observer.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/components/cookie-jar-selector.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/components/external-app-blocker.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/components/torbutton-logger.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/components/cssblocker.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/components/window-mapper.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/components/certDialogsOverride.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/components/nsSessionStore35.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/components: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/LICENSE: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/CHANGELOG: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/install.rdf: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/defaults/preferences/preferences.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/defaults/preferences: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/defaults: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}/chrome.manifest.nojar: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/{e0204bd5-9d31-402b-a99d-a6aa8ffebdca}: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/defaults/preferences/bpprefs.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/defaults/preferences: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/defaults: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla/extensions: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/.mozilla: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/tor: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/icons/mozicon128.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/icons/mozicon16.xpm: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/icons/document.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/icons/mozicon50.xpm: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/icons/updater.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/icons: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/modules/distribution.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/modules/DownloadLastDir.jsm: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/modules/debug.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/modules/DownloadUtils.jsm: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/modules/utils.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/modules/openLocationLastURL.jsm: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/modules/WindowDraggingUtils.jsm: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/modules/PluralForm.jsm: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/modules/SpatialNavigation.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/modules/ISO8601DateUtils.jsm: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/modules/XPCOMUtils.jsm: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/modules/PlacesDBUtils.jsm: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/modules/Microformats.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/modules: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libsoftokn3.chk: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libssl3.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/README.txt: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/old-homepage-default.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libxpcom.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libplds4.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libnssutil3.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/classic.manifest: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/icons/default/default48.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/icons/default/default16.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/icons/default/default32.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/icons/default: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/icons: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/comm.manifest: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/reporter.jar: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/classic.jar: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/browser.manifest: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/toolkit.jar: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/en-US.manifest: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/pippki.jar: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/comm.jar: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/toolkit.manifest: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/browser.jar: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/en-US.jar: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/pippki.manifest: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome/reporter.manifest: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/chrome: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libnspr4.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/crashreporter: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/firefox: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/removed-files: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/dictionaries/en-US.aff: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/dictionaries/en-US.dic: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/dictionaries: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/crashreporter.ini: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/crashreporter-override.ini: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/firefox-bin: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libfreebl3.chk: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/Data: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsSessionStore.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsSafebrowsingApplication.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/aboutCertError.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/txEXSLTRegExFunctions.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsSearchSuggestions.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsBadCertHandler.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsPrivateBrowsingService.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsMicrosummaryService.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/fuelApplication.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/libbrowserdirprovider.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/FeedWriter.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/aboutRights.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsAddonRepository.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/jsconsole-clhandler.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsBlocklistService.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsUrlClassifierLib.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsUpdateService.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsFilePicker.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsDefaultCLH.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/libbrowsercomps.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsBrowserGlue.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsProxyAutoConfig.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsLoginInfo.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsLivemarkService.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsHandlerService.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/FeedProcessor.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsPlacesDBFlush.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/pluginGlue.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsPlacesTransactionsService.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsLoginManager.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/libimgicon.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsTryToClose.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/FeedConverter.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/aboutSessionRestore.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsContentDispatchChooser.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsSidebar.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsContentPrefService.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/aboutRobots.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/NetworkGeolocationProvider.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsTaggingService.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/browser.xpt: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsDownloadManagerUI.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsURLFormatter.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/libdbusservice.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsSearchService.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsSetDefaultBrowser.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/storage-mozStorage.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsSessionStartup.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsUrlClassifierListManager.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsLoginManagerPrompter.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/WebContentConverter.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsExtensionManager.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsBrowserContentHandler.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsHelperAppDlg.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/nsWebHandlerApp.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/aboutPrivateBrowsing.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components/storage-Legacy.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/components: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/mozilla-xremote-client: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/greprefs/all.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/greprefs/xpinstall.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/greprefs/security-prefs.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/greprefs: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/searchplugins/eBay.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/searchplugins/creativecommons.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/searchplugins/amazondotcom.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/searchplugins/answers.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/searchplugins/google.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/searchplugins/wikipedia.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/searchplugins/yahoo.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/searchplugins: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/platform.ini: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/run-mozilla.sh: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libsoftokn3.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libplc4.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libnssdbm3.chk: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libnssckbi.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libsmime3.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libxul.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libnss3.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/update.locale: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/updater.ini: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libfreebl3.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libsqlite3.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/plugins/libnullplugin.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/plugins: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/Throbber-small.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libnssdbm3.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/application.ini: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/libmozjs.so: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/extensions: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/ua.css: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/dtd/mathml.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/dtd/xhtml11.dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/dtd: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/arrowd.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-add-row-after.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-add-row-before-hover.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/contenteditable.css: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-remove-row-active.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/grabber.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/charsetalias.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-add-column-after-hover.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/langGroups.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-remove-column-active.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/language.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-remove-row-hover.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-add-column-before-hover.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-add-row-after-active.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/fonts/mathfontSTIXNonUnicode.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/fonts/mathfont.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/fonts/mathfontSTIXSize1.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/fonts/mathfontStandardSymbolsL.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/fonts/mathfontUnicode.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/fonts: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-add-column-before-active.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/arrow.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/html/folder.png: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/html: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/html.css: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/viewsource.css: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/broken-image.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-remove-row.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-remove-column-hover.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-add-column-after-active.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-add-column-after.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-add-row-before.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-remove-column.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/mathml.css: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/unixcharset.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-add-row-before-active.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/svg.css: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/entityTables/html40Symbols.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/entityTables/mathml20.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/entityTables/html40Latin1.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/entityTables/htmlEntityVersions.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/entityTables/transliterate.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/entityTables/html40Special.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/entityTables: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-add-row-after-hover.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/quirk.css: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/loading-image.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/designmode.css: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/charsetData.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/forms.css: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/EditorOverride.css: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/hiddenWindow.html: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res/table-add-column-before.gif: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/res: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/updater: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/browserconfig.properties: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/autoconfig/prefcalls.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/autoconfig/platform.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/autoconfig: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/profile/localstore.rdf: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/profile/chrome/userContent-example.css: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/profile/chrome/userChrome-example.css: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/profile/chrome: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/profile/bookmarks.html: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/profile/prefs.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/profile/mimeTypes.rdf: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/profile: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/pref/reporter.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/pref/channel-prefs.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/pref/firefox.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/pref/firefox-branding.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/pref/firefox-l10n.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults/pref: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/defaults: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox/blocklist.xml: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/Firefox: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/vidalia: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App/polipo: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/App: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Data/Polipo/polipo.conf: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Data/Polipo: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Data/profile/bookmarks.html: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Data/profile/prefs.js: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Data/profile: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Data/Tor/torrc: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Data/Tor/geoip: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Data/Tor: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Data/profiles.ini: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Data/Vidalia/vidalia.conf: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Data/Vidalia: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Data: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/tmp: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/start-tor-browser: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libQtXml.so: Cannot create symlink to `libQtXml.so.4.6.2': Operation not permitted
tar: tor-browser_en-US/Lib/libQtGui.so: Cannot create symlink to `libQtGui.so.4.6.2': Operation not permitted
tar: tor-browser_en-US/Lib/libQtGui.so.4.6: Cannot create symlink to `libQtGui.so.4.6.2': Operation not permitted
tar: tor-browser_en-US/Lib/libevent_core-1.4.so.2: Cannot create symlink to `libevent_core-1.4.so.2.1.3': Operation not permitted
tar: tor-browser_en-US/Lib/libQtGui.so.4: Cannot create symlink to `libQtGui.so.4.6.2': Operation not permitted
tar: tor-browser_en-US/Lib/libcrypto.a: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libevent-1.4.so.2: Cannot create symlink to `libevent-1.4.so.2.1.3': Operation not permitted
tar: tor-browser_en-US/Lib/libQtNetwork.so: Cannot create symlink to `libQtNetwork.so.4.6.2': Operation not permitted
tar: tor-browser_en-US/Lib/libQtCore.so.4: Cannot create symlink to `libQtCore.so.4.6.2': Operation not permitted
tar: tor-browser_en-US/Lib/libssl.so.0.9.8: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libpng14.so: Cannot create symlink to `libpng14.so.14.2.0': Operation not permitted
tar: tor-browser_en-US/Lib/libQtNetwork.so.4.6: Cannot create symlink to `libQtNetwork.so.4.6.2': Operation not permitted
tar: tor-browser_en-US/Lib/libevent_core.so: Cannot create symlink to `libevent_core-1.4.so.2.1.3': Operation not permitted
tar: tor-browser_en-US/Lib/libz/libz.so.1.2.3: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libz/libz.so: Cannot create symlink to `libz.so.1.2.3': Operation not permitted
tar: tor-browser_en-US/Lib/libz/libz.so.1: Cannot create symlink to `libz.so.1.2.3': Operation not permitted
tar: tor-browser_en-US/Lib/libz: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libQtCore.so: Cannot create symlink to `libQtCore.so.4.6.2': Operation not permitted
tar: tor-browser_en-US/Lib/libQtXml.so.4.6.2: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libcrypto.so: Cannot create symlink to `libcrypto.so.0.9.8': Operation not permitted
tar: tor-browser_en-US/Lib/libevent_extra-1.4.so.2.1.3: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libevent_extra.so: Cannot create symlink to `libevent_extra-1.4.so.2.1.3': Operation not permitted
tar: tor-browser_en-US/Lib/libQtCore.so.4.6: Cannot create symlink to `libQtCore.so.4.6.2': Operation not permitted
tar: tor-browser_en-US/Lib/libQtXml.so.4.6: Cannot create symlink to `libQtXml.so.4.6.2': Operation not permitted
tar: tor-browser_en-US/Lib/libQtNetwork.so.4: Cannot create symlink to `libQtNetwork.so.4.6.2': Operation not permitted
tar: tor-browser_en-US/Lib/libpng14.so.14: Cannot create symlink to `libpng14.so.14.2.0': Operation not permitted
tar: tor-browser_en-US/Lib/libssl.a: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libevent-1.4.so.2.1.3: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libpng14.so.14.2.0: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libssl.so: Cannot create symlink to `libssl.so.0.9.8': Operation not permitted
tar: tor-browser_en-US/Lib/libQtCore.so.4.6.2: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libevent_core-1.4.so.2.1.3: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libQtXml.so.4: Cannot create symlink to `libQtXml.so.4.6.2': Operation not permitted
tar: tor-browser_en-US/Lib/libcrypto.so.0.9.8: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libevent_extra-1.4.so.2: Cannot create symlink to `libevent_extra-1.4.so.2.1.3': Operation not permitted
tar: tor-browser_en-US/Lib/libQtGui.so.4.6.2: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libQtNetwork.so.4.6.2: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Lib/libevent.so: Cannot create symlink to `libevent-1.4.so.2.1.3': Operation not permitted
tar: tor-browser_en-US/Lib: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Polipo/README: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Polipo/COPYING: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Polipo: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Qt/LICENSE.GPL3: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Qt/LICENSE.LGPL: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Qt: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Tor/README: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Tor/LICENSE: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Tor: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Vidalia/LICENSE-GPLV2: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Vidalia/CREDITS: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Vidalia/LICENSE: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Vidalia/LICENSE-OPENSSL: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Vidalia/LICENSE-GPLV3: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Vidalia/LICENSE-LGPLV3: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/Vidalia: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs/README-TorBrowserBundle: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US/Docs: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: tor-browser_en-US: Cannot change ownership to uid 1000, gid 1000: Operation not permitted
tar: Exiting with failure status due to previous errors

```


Any idea how to fix this?

---

### Post by FuturePilot on 2010-06-15
Because the flash drive is probably formated as FAT which does not know what Unix file permissions are. Try extracting it to a temporary directory and then manually copy it on to the flash drive.

---

### Post by Bachstelze on 2010-06-15
> **FuturePilot said:**
> Because the flash drive is probably formated as FAT which does not know what Unix file permissions are. Try extracting it to a temporary directory and then manually copy it on to the flash drive.

The permissions shouldn't be a problem, but it also tries to create some symlinks, which might be required for it to work. In that case, the only solution would be to format the drive in a Linux filesystem like ext.

---

### Post by PDA1 on 2010-06-15
Because the flash drive is probably formated as FAT which does not know  what Unix file permissions are. Try extracting it to a temporary  directory and then manually copy it on to the flash drive.



....gave it a try but it didn't work.  Some error message came up.  I tired of trying.

Thanks for the help.

---

### Post by bodhi.zazen on 2010-06-15
> **PDA1 said:**
> Because the flash drive is probably formated as FAT which does not know  what Unix file permissions are. Try extracting it to a temporary  directory and then manually copy it on to the flash drive.



....gave it a try but it didn't work.  Some error message came up.  I tired of trying.

Thanks for the help.

Where are you extracting the archive to ?

The error message is most likely because you are extracting the archive to either a FAT or NTFS partition.

Can you try extracting it in your home directory ?

---

### Post by PDA1 on 2010-06-15
I tried it....here's the error I got-  Filesystem does not support symbolic links

---

### Post by bodhi.zazen on 2010-06-16
> **PDA1 said:**
> I tried it....here's the error I got-  Filesystem does not support symbolic links

The download works perfectly here.

What file system are you using and where are you extracting the archive ?

---

