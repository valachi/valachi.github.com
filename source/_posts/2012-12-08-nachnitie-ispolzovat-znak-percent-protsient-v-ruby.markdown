---
layout: post
title: "Начните использовать знак процента в Ruby"
date: 2012-12-08 19:03
comments: true
categories:
---

[1]: http://teohm.github.com/blog/2012/10/15/start-using-ruby-percent-notation/ "original"
[2]: https://github.com/teohm/a-dip-in-ruby/blob/master/spec/percent_notation_spec.rb "example"

Если в ежедневной работе вы редко используете знак % в коде, то вот несколько приемов, которые вы можете использовать.
Помимо всем известного

{% codeblock lang:ruby %}
	[1] pry(main)> %w(apple banana pineapple)
	=> ["apple", "banana", "pineapple"]
{% endcodeblock %}

конечно.

<!-- more -->

## Используйте любой символ в качестве разделителя

{% codeblock lang:ruby %}
%(any alpha-numeric) #=> "any alpha-numeric"
%[char can be] #=> "char can be"
%%used as% #=> "used as"
%!delimiter\!! # escape '!' literal
{% endcodeblock %}



## Не эскейпите скобки, даже если разделителями служат такие же скобки

{% codeblock lang:ruby %}
%( (pa(re(nt)he)sis) ) #=> "(pa(re(nt)he)sis)"
%[ [square bracket] ]  #=> "[square bracket]"
%{ {curly bracket} }   #=> "{curly bracket}"
%< <pointy bracket> >  #=> "<pointy bracket>"
%< \<this works as well\> >  #=> "<this works as well>"
{% endcodeblock %}

## Модификаторы для String, Regex, Array, Symbol, Shell команд

{% codeblock lang:ruby %}
%(interpolated string (#{ "default" }))
  #=> "interpolated string (default)"
%Q(interpolated string (#{ "default" }))
  #=> "interpolated string (default)"
%q(non-interpolated string)
  #=> "non-interpolated string"
%r(#{ "interpolated" } regexp)i
  #=> /interpolated regexp/i
%w(non-interpolated\ string  separated\ by\ whitespaces)
  #=> ['non-interpolated string', 'separated by whitespaces']
%W(interpolated\ string #{ "separated by whitespaces" })
  #=> ['interpolated string', 'separated by whitespaces']
%s(non-interpolated symbol)
  #=> :'non-interpolated symbol'
%x(echo #{ "interpolated shell command" })
  #=> "interpolated shell command\n"
{% endcodeblock %}

*В примере на строке 9 автор, очевидно, автор имел в виду "non-interpolated Array of words, separated by whitespaces" вместо "non-interpolated String"*

[Здесь][2] можно посмотреть еще несколько примеров с тестами	.

[Источник][1]