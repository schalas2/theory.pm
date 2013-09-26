---
layout: post
title: "Lexical Subroutines"
date: 2013-09-25 20:12
comments: true
external-url: http://rjbs.manxome.org/rubric/entry/2016
categories: [syntax]
---

Ricardo Signes:

> One of the big new experimental features in Perl 5.18.0 is lexical
>  subroutines. In other words, you can write this:
>
>     my sub quickly { ... }
>     my @sorted = sort quickly @list;
> 
>     my sub greppy (&@) { ... }
>     my @grepped = greppy { ... } @input;
>
> These two examples show cases where lexical *references* to anonymous
> subroutines would not have worked. The first argument to `sort` must be a
> block or a subroutine *name*, which leads to awful code like this:
> 
>     sort { $subref->($a, $b) } @list
> 
> With our greppy, above, we get to benefit from the parser-affecting
> behaviors of subroutine prototypes.

My favorite tidbit about this feature? Because lexical subs are *lexical,* and
method-dispatch is *package*-based, lexical subs are not subject to method
lookup and dispatch! This just might alleviate the confusion of methods and
subs, as [chromatic complained about just yesterday]. Probably doesn't solve
the problem for imported subs, though.

[chromatic complained about just yesterday]: http://www.modernperlbooks.com/mt/2013/09/functions-shouldnt-be-methods-yet-another-reminder.html



