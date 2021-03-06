---
layout: post
title: Counting Subscribers
subtitle: "Feedburner became popular by tracking the number of subscribers. Even if decentralization makes that hard, it's still possible to get some data. Here's how to achieve that with SubToMe."

author:
  name: Julien Genestoux
  link: http://ouvre-boite.com/
  image: http://www.gravatar.com/avatar/b30ce50678f0e934eaa6697425c59dd7?s=256
  bio: Co-founder, Superfeedr.
---

Right or wrong, the **amount of "followers"** is often used as a proxy for *popularity* and *importance*. We believe this is the reasons why [Feedburner](http://www.feedburner.com/‎) quickly got so popular: it gave publishers and bloggers an interesting metric that they could compare. Years later, the number of followers on Twitter is also prominent on [their follow buttons](https://dev.twitter.com/docs/follow-button).

Now, since SubToMe is fully **decentralized** (publishing applications and subscribing applications are unaware of each other), it's really hard to provide accurate analytics (not that Feedburner's stats were accurate either... but that's another story). However, there is one thing that SubToMe can tell the publisher: that a *susbcription happened*.

Basically, everytime someone clicks on the SubToMe button you've put on your site, SubToMe will *trigger a Javascript event* that you should listen to. The event incldues the following information:

* **feeds**: the list of feeds to which the user may have subscribed
* **resource**: the HTTP resource related to the subscription
* **The app** used to subscribe: its name and its url.

Here is some sample code:
<code>
  window.addEventListener("message", function(event) {
    if (event.origin !== "https://www.subtome.com")
    return;
    // do something with event.data.subscription
  });
</code>

By default, the [load.js](https://www.subtome.com/load.js) file, which is the default way to load the SubToMe button, will also trigger a [Google Analytics](http://www.google.com/analytics/) (if your site uses it) event to tell you that somebody subscribed to your feed! 


