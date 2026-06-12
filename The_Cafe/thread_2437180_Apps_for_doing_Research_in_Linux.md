---
title: "Apps for doing Research in Linux"
date: 2020-02-19
forum: The Cafe
---

### Post by astraadria4ari on 2020-02-19
On the topic of research and apps that help document research and write research papers in Linux (Fedora Workstation 31) this is my experience and opinion:


LibreOffice is most compatible with the all formats for research conferences and journal paper publication, it even supports LaTex format. [https://www.libreoffice.org/download/download/](https://www.libreoffice.org/download/download/)


Gnome Latex works great and is one of the best apps for Latex format. [https://github.com/GNOME/gnome-latex](https://github.com/GNOME/gnome-latex)


Zotero is a great application for research for references and bibliographies organization, supports Open ID login by OpenID Foundation [https://www.zotero.org](https://www.zotero.org) 


Atom is one of the best text editors for code writing, you can &#8220;hack it&#8221; (legally and supported by FOSS licence) and make it your own to best suite you + post it on github [https://atom.io](https://atom.io)


(I hope Microsoft will not change that and give priority to their VSCode text editor)


DataHub (Guthub for datasets) CLI tool works in Linux, website works fine, they should have a graphical tool soon (not sure if CLI works in other Operating Systems) [https://datahub.io](https://datahub.io)


(Get Archive [https://github.com/datopian/data-cli/releases/download/v0.9.5/data-linux.gz](https://github.com/datopian/data-cli/releases/download/v0.9.5/data-linux.gz)


unzip archive, make file executable &#8220;chmod +rwx data-linux&#8221; or &#8220;chmod 777 data linux&#8221; and start from terminal.)


Joplin is great note taking to do list app, supporting markdown format [https://joplinapp.org](https://joplinapp.org)
syncing with NextCloud [https://nextcloud.com](https://nextcloud.com) (other sync options supported).


Firefox one of the best browsers that respect privacy and is not chromium based. [https://www.mozilla.org/en-US/firefox/new/](https://www.mozilla.org/en-US/firefox/new/)

**My Recommended Linux Operating system is Fedora Workstation with software from [https://labs.fedoraproject.org](https://labs.fedoraproject.org) or just use Fedora Labs from start.**
**My Recommendation based on experience for doing research in Linux (Fedora Workstation) is:**
**LibreOffice + Gnome Latex + Zotero + Atom (and github) + datahub CLI + Joplin + Firefox**


Any comments or advice are welcome here, I am always happy to learn about new FOSS (free and open source software) applications that are used in research today.

**My Current Goal is to try install and test out all of this apps in the latest Ubuntu (and the next ubuntu LTS once it is out) any advice is welcome.**


Regards, Alex

---

### Post by TheFu on 2020-02-19
Please don't recommend chmod +rwx or chmod 777.  
That is a good way to get hacked.  Only people who don't understand basic file/directory permissions would ever use that.  644/640 for data files and 755/750 for programs and directories.  Please.

You left out vim, by far the most useful research tool I know.

---

### Post by mastablasta on 2020-02-20
well depends on what kind of research you do.i needed something like PSPP, but it needs to develop more.

---

### Post by 1clue on 2020-03-01
+1 for everything @TheFu said.

I would have included git, with or without github.

I would also have included tmux.

While it's a little less conventional, you might be able to use ctags with documentation. Tex is one of the supported languages, for example. And [https://stackoverflow.com/questions/25742396/creating-ctags-extension-for-markdown](https://stackoverflow.com/questions/25742396/creating-ctags-extension-for-markdown)

The trio of tmux, vim and ctags are hugely effective development tools, and if you're using them anyway then there are lots of markdown/asciidoc type languages out there that can work with latex-style engines. And with github, where github does the translation and update of a web site when you check the project in.

For those people who are willing to step outside of the "free software" realm, I also really like Sublime Text. Next to vim, it's the best text editor out there IMO.

---

