# Easy to write and understand templating language
Simple template language which can be converted to html. It is intended to be used with Vue or Angular.

The main idea is to be able to write clear and readable code because html contains too much boilerplate and it is very hard to understand its meaning.

The language is able to convert this:
```
div.row {
    div.col {
        form :submit=submit() {
            input type=number v-model=zzz :class="[{q: 'zz'}, zz, dd]" {}

            select.tst-z v-model=choose {
                option v-for="v in options" :value=v.id {
                    'title: {{v.title}}'
                }
            }

            button.btn.btn-primary { 'Submit' }
        }
    }
}
```
into this:
```html
<div class="row">
    <div class="col">
        <form :submit="submit()">
            <input type="number" v-model="zzz" :class="[{q: 'zz'}, zz, dd]" />
            <select v-model="choose" class="tst">
                <option v-for="v in options" :value="v.id">title: {{v.title}}</option>
            </select>

            <button class="btn btn-primary">Submit</button>
        </form>
    </div>
</div>
```
## Main rules
- This is just an html in disguise - just more simplified and less verbose (You don't have to think of it as another language)
- There are two possible elements: html element or text
- The html element always ends with {} (if you forget them this element will include all other elements until it finds {}) and inside are all elements or text it contains
- Text is always inside single quotes
- The html emenet may have classes added directly to the element (div.some-class {}) or as class attribute (div class=some-class {})
- The html element may have attributes. If the attribute value does not contain space you can write it without double quotes (div id=my-id {}) (div style="width: 100%; padding: 0;" {})

## Why another template language?
Why create another template language when we have others like [jade](http://jade-lang.com/) and [pug](https://github.com/pugjs/pug)?

From my point of view python-like languages look simple but actually are very hard to read and understand. And you can never be sure where the code block ends :)

For me the difference between pug and easy-html is like the difference between sass and scss (guess why no one uses sass :))

The language will not have any logical constructs (like "if", "foreach") because it is aimed to be used with Vue or Angular.

The language is not ready yet but I am working actively on it.