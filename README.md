# Habbo Hotel group badges
This documentation explains how badges are structured and how they are hashed.

## Badge structure
Badges typically consist of <b>0-n</b> badge parts. Badge parts are divided in 3 different types:
- <b>b</b>: Base parts
- <b>s</b>: Additional parts (1-99)
- <b>t</b>: Additional parts (100-199)

Both types of badge parts are built using 1 letter and 5 digits:

<table>
<tr>
<td><b>Type</b></td>
<td><b>Badge part ID</b></td>
<td><b>Color</b></td>
<td><b>Position</b></td>
</tr>
<tr>
<td>b/s/t</td>
<td>00-99</td>
<td>01-24</td>
<td>0-8</td>
</tr>
</table>

All 3 badge parts are optional, but when a badge part is added, it <b>must</b> contain the letter and <b>exactly 5</b> digits. If your `Badge Part ID` or `Color` are below 10, add a leading 0.

### The difference between types

The main difference between `b` and `s` or `t` is that `b` can only display base parts, and the others can only display additional parts. It is also worth noting that a badge can contain multiple base parts.

There's also a slight difference between `s` and `t`. There's between 100 and 200 different additional parts available in Habbo, but a badge part only takes 5 digits, so `Badge part ID` can't be more than 99. To still use an additional part that goes above 99, we can use `t`. When `t` is set to 00, that equals `Badge part ID` 100, 10 equals `Badge part ID` 110, etc. For `Badge part ID` 1 to 99, you can use `s`.

### Badge part IDs

A `Badge part ID` is a 2-digit number that represents a certain image or shape in your badge. Base- and additional parts both have their own IDs. A few of them are displayed below.

#### Base
<table>
<tr>
<td><b>ID 1</b></td>
<td><b>ID 2</b></td>
<td><b>ID 3</b></td>
</tr>
<tr>
<td><img src="https://www.habbo.nl/habbo-imaging/badge/b01010006791b2fcf18535db5c46607b2bce63"></td>
<td><img src="https://www.habbo.nl/habbo-imaging/badge/b0201007a27a440faa05d1e488ff92a078cbaa"></td>
<td><img src="https://www.habbo.nl/habbo-imaging/badge/b03010ddcf06faef8477d20f896d364a201fd5"></td>
</tr>
</table>

#### Additional
<table>
<tr>
<td><b>ID 1</b></td>
<td><b>ID 2</b></td>
<td><b>ID 3</b></td>
</tr>
<tr>
<td><img src="https://www.habbo.com/habbo-imaging/badge/s010142f93213435a0f8a2ee6e57d326acb761"></td>
<td><img src="https://www.habbo.com/habbo-imaging/badge/s02014077252640988ad6ffbfbe81b9d7caa05"></td>
<td><img src="https://www.habbo.com/habbo-imaging/badge/s030140f7437c1b7f92d36acb53d331a834859"></td>
</tr>
</table>

### Colors

A `Color` is a 2-digit number that represents the color of a badge part. There is 24 different colors in total. Note that not all badge parts can be colored. In that case, any number will return the same default color. An example of a non-colorable badge part is displayed below.

<img src="https://www.habbo.nl/habbo-imaging/badge/t41014935ea23c7318fc7943932593160409e7"> 

### Positions & Layers

A `Position` is a single digit that represents the position of a badge part in your badge. There is 9 different possible positions (0-8), 0 being the upper left corner, 4 being the center and 8 being the bottom right corner. Some bigger badge parts will always be centered, regardless of the set position. A badge demonstrating all possible positions is displayed below.

<img src="https://www.habbo.nl/habbo-imaging/badge/s68010s69011s70012s71013s72014s73015s74016s75017s76018bdd473f066504f3341d056d5a1fb664c">

A badge also has layers. That means that badge parts can overlap other badge parts. A badge part on layer 1 will overlap the part on layer 0, a part on layer 2 will overlap the one on layer 1, etc. What layer a badge part is on, is determined by the order they are in. For example, the order is like this: `[part_a][part_b]`, here, `part_a` is on layer 0, and `part_b` is on layer 1. Layers apply to any type of badge part.

### Example structures

This list of examples demonstrates how to build structures for a badge.

#### Correct structures
<table>
<tr>
<td><b>Image</b></td>
<td><b>Structure</b></td>
<td><b>Explained</b></td>
</tr>
<tr>
<td><img src="https://www.habbo.com/habbo-imaging/badge/b0312011748398e35232e4bf1ae3a8b399b947"></td>
<td><code>b</code><code>03</code><code>12</code><code>0</code></td>
<td>A single base part with ID 03, color 12 and position 0</td>
</tr>
<tr>
<td><img src="https://www.habbo.com/habbo-imaging/badge/b01200s0610440b349c7c406fb2c9545f7f5f641fd99"></td>
<td><code>b</code><code>01</code><code>20</code><code>0</code><code>s</code><code>06</code><code>10</code><code>4</code></td>
<td>Base 1 with color 20 and 1 additional part with ID 6, color 10 and position 4</td>
</tr>
<tr>
<td><img src="https://www.habbo.com/habbo-imaging/badge/b01200s84033s86034s970359be7b0f7040a1f694e08c7307e6feeac"></td>
<td><code>b</code><code>01</code><code>20</code><code>0</code><code>s</code><code>84</code><code>03</code><code>3</code><code>s</code><code>86</code><code>03</code><code>4</code><code>s</code><code>97</code><code>03</code><code>5</code></td>
<td>Same base as above, with 3 additional parts on positions 3, 4 and 5, making the word 'GIT' together</td>
</tr>
<tr>
<td><img src="https://www.habbo.com/habbo-imaging/badge/b01030b030303a074ec3f2ab2adb13ee6c4e1833ad62"></td>
<td><code>b</code><code>01</code><code>03</code><code>0</code><code>b</code><code>03</code><code>03</code><code>0</code></td>
<td>Example of a badge with multiple base parts</td>
</tr>
<tr>
<td><img src="https://www.habbo.com/habbo-imaging/badge/s84033s86034s9703585d8e114ae901a0051837a76efb46021"></td>
<td><code>s</code><code>84</code><code>03</code><code>3</code><code>s</code><code>86</code><code>03</code><code>4</code><code>s</code><code>97</code><code>03</code><code>5</code></td>
<td>Same as #3, except this badge doesn't have any base parts</td>
</tr>
<tr>
<td><img src="https://www.habbo.com/habbo-imaging/badge/fc6a5baf8af71b99d1ae37eb24114307"></td>
<td><code></code></td>
<td>Completely empty structure, results into an empty badge</td>
</tr>
</table> 

## Structure hashing

Structure hashing is a more technical matter. How it works exactly is explained in this part of the documentation. A Habbo imaging URL typically looks like: `:server/habbo-imaging/:imageType/:struct:hash`

Where
<table>
<tr>
<td>:server</td>
<td>Is the address of the server. For example https://www.habbo.com</td>
</tr>
<tr>
<td>:imageType</td>
<td>Is the type of image you are requesting. In this case that is 'badge'</td>
</tr>
<tr>
<td>:struct</td>
<td>Is the badge structure that has been explained </td>
</tr>
