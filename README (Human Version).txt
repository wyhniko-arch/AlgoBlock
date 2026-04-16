各位好啊，我是人类，我来说几句吧。
首先别看README.md，那哥们AIGC的，信息熵很低，看docs最新的技术文档会稍微好点。
我理解他在干什么，但是我并不想炫太多专业术语，我觉得几句话就能讲清楚的事情，没必要写得像个深奥的论文。

它的本质是 “函数式流处理的游戏化”。目前是 $f(List) \to List$ 的线性处理。
最终幻想是能通过指令嵌套，将复杂的算法逻辑（比如某大神在 ACM 里的那些神仙操作）封装成一个个“原子积木”，玩家可以通过在游戏特定一些关卡中，调用额外的、由MOD制作者制作的一些积木，它们有全新的名称、参数列表、内部处理数据的逻辑、以及一种或多种输出，
但显然在将算法拆得有多散和中间解作为输入如何通过一个统一的接口去实现这些东西很棘手，所以我们只打算把一类线性变化的基础算法做成游戏，避免暴露在外部的循环、选择、递归、等等。

爽点就是它一定会很酷！在一个酷炫的、带光影特效的终端里，仿佛在写 Lisp 一样，一行指令解决一个“鬼题”。
然后这个项目是糊作业，所以用了反射之类的，还用了一些非主流的渲染工具链，模块化和解耦其实牺牲了关卡设计的部分自由，但这毕竟就是个作业！所以它必须越规范越容易拿分，有时需要杀鸡用牛刀。
这是为了在答辩时让老师觉得我们“很有工程素养”。

“怎么算”和“怎么画”是分开的。意味着你写一个积木时，不需要懂 OpenGL，只要懂 Java 逻辑就行，这是好消息，也是坏消息，因为这意味着你没法去设计特效。
我个人只要有一个能在屏幕任意位置修改任意像素的方法，就可以写任何效果出来，他写的这一块我马上再梳理一下，他不写注释害得我看了一夜。

Mod 系统，我认为吧，这是一个“开放世界”的算法游戏。MOD引擎相当于插座，具体的积木是插头。你可以写自己的库，实现对一整个关卡从谜面到谜底的掌控，以及对那些“照着答案出题”的复杂逻辑积木块的设计。

渲染管线，这就是我们要装逼的地方。风格的灵感来源有《黑客帝国》、游戏《Hack net》等，光标会像安装了VScode Animation Extention那样有个残影，还有更多酷炫效果待添加。
但如果搞数据驱动感觉自由度低了点，有点为了踩得分点而做的了，不是很高效。

目前的痛点：
接口太窄。目前的 API 只能进出一串数，当前版本够用，但是MOD咋办呢？可能要扩展一下 EvalContext，人话就是输出不作为积木的返回值，而是作为可以被存储的各种新数据材料，可以作为后续指令的参数。
我个人希望算法的复杂度能实时反映在特效上，没有中间过程说得情商高点叫硬核，说得好听点叫模拟OJ，直白点叫没时间，难听点叫不是得分点。

这个文档不能让老师看到吧？你们觉得呢？

Hello everyone, I am a human, let me say a few words. 
First, don't just look at README.md, that's all from AIGC, the information entropy is very low. It's a bit better to check the latest technical documents in docs. 
I understand what he is doing, but I don't want to flaunt too many technical terms. I think things that can be explained in a few sentences don't need to be written like an obscure paper.

Its essence is 'gamified functional stream processing'. Currently, it is a linear process of $f(List) to List$. 
The ultimate fantasy is to be able to nest commands to encapsulate complex algorithmic logic (such as those god-level operations from ACM by some master) into 'atomic building blocks'. Players can use these blocks in specific game levels, calling extra blocks created by MOD makers, which have new names, parameter lists, internal data processing logic, and one or more outputs. 
But obviously, breaking algorithms so finely and using intermediate solutions as input through a unified interface is very tricky, so we only plan to make a type of linear-change basic algorithm as a game, avoiding exposing external loops, selections, recursions, and so on.

The thrill is that it will definitely be cool! In a flashy, light-and-shadow terminal, it feels like writing Lisp, solving a 'tricky problem' with one line of command. 
This project is basically a half-baked assignment, so it uses reflections and some non-mainstream rendering toolchains. Modularization and decoupling actually sacrifice some freedom in level design, but this is just an assignment! So it must be as standardized as possible to get high marks, sometimes using a sledgehammer to crack a nut.
This was to make the professors think we had "a lot of engineering skills" during the defense.

'How to calculate' and 'how to render' are separate. This means that when you create a building block, you don't need to know OpenGL, just understand Java logic. This is good news and bad news because it also means you can't design special effects. 
Personally, as long as I have a way to modify any pixel at any position on the screen, I can create any effect. I will go over the part he wrote immediately since he didn't write comments and I spent a whole night figuring it out.

MOD system: in my view, this is an 'open world' algorithm game. The MOD engine is like a socket, and the specific blocks are the plugs. You can write your own library, control an entire level from puzzle to solution, and design complex logic blocks for those 'create puzzles following the answers'.

Rendering pipeline: this is where we want to show off. The stylistic inspiration comes from 'The Matrix' and the game 'Hacknet'. The cursor will have a trailing effect like installing the VSCode Animation Extension, and more cool effects are to be added. 
However, if we go data-driven, the freedom feels limited, kind of just done to score points, not very efficient.

Current pain points:
The interface is too narrow. The current API can only handle a string of numbers in and out. It's enough for the current version, but what about MOD? We might need to expand the EvalContext. In plain language, this means making the output not just the return value of a block, but various new data materials that can be stored and used as parameters for subsequent instructions. Personally, I hope the complexity of the algorithm can be reflected in the effects in real time. In more refined terms, this is called 'hardcore'; nicely put, it's like simulating an OJ; plainly, it means no time; in harsh terms, it's not a scoring point. 

This document shouldn’t be shown to the teacher, right? What do you guys think?.