---
id: 5f0d4ab1b435f13ab6550052
title: Part 51
challengeType: 0
isHidden: true
---

## Description
<section id='description'>

Next, you are going to add some new form `input` elements, so add another `fieldset` element directly below the current `fieldset` element.

</section>

## Tests
<section id='tests'>

```yml
tests:
  - text: "Your new `fieldset` element should have an opening tag. Opening tags have this syntax: `<elementName>`."
    testString: assert( document.querySelectorAll('fieldset').length >= 2 );
  - text: You should only add one opening `fieldset` tag. Please remove any extras.
    testString: assert( document.querySelectorAll('fieldset').length === 2 );
  - text: Your new `fieldset` element should have a closing tag. Closing tags have a `/` just after the `<` character.
    testString: assert( code.match(/<\/fieldset>/g).length >= 2 );
  - text: You should only add one closing `fieldset` tag. Please remove any extras.
    testString: assert( code.match(/<\/fieldset>/g).length === 2 );
  - text: The second `fieldset` element should not be nested in the first `fieldset` element.
    testString: |
      const childrenOf1stFieldset = [ ...document.querySelector('form > fieldset').children ];
      const foundElems = childrenOf1stFieldset.filter(child => {
        return child.nodeName === 'FIELDSET';
      });
      assert( foundElems.length === 0 );
  - text: Both `fieldset` elements should be above the text field and its associated `label` element. They are out of order.
    testString: |
      const formChildren = $('form')[0].children;
      assert(
        formChildren[0].nodeName === 'FIELDSET' &&
        formChildren[1].nodeName === 'FIELDSET' &&
        formChildren[2] && formChildren[2].nodeName === 'INPUT' &&
        formChildren[2].getAttribute('type') === 'text'
      );
  - text: Your new `fieldset` element should be below the existing `fieldset` element. You have them in the wrong order.
    testString: |
      const fieldsetChildren = [...document.querySelectorAll('fieldset')].map(elem => elem.children);
      assert( fieldsetChildren[0].length > fieldsetChildren
      [1].length );

```

</section>

## Challenge Seed
<section id='challengeSeed'>
<div id='html-seed'>

```html
<html>
  <body>
    <h1>CatPhotoApp</h1>
    <main>
      <section>
        <h2>Cat Photos</h2>
        <!-- TODO: Add link to cat photos -->
        <p>Click here to view more <a target="_blank" href="https://freecatphotoapp.com">cat photos</a>.</p>
        <a href="https://freecatphotoapp.com"><img src="https://bit.ly/fcc-relaxing-cat" alt="A cute orange cat lying on its back."></a>
      </section>
      <section>
        <h2>Cat Lists</h2>
        <h3>Things cats love:</h3>
        <ul>
          <li>cat nip</li>
          <li>laser pointers</li>
          <li>lasagna</li>
        </ul>
        <figure>
          <img src="https://bit.ly/fcc-lasagna" alt="A slice of lasagna on a plate.">
          <figcaption>Cats <em>love</em> lasagna.</figcaption>  
        </figure>
        <h3>Top 3 things cats hate:</h3>
        <ol>
          <li>flea treatment</li>
          <li>thunder</li>
          <li>other cats</li>
        </ol>
        <figure>
          <img src="https://bit.ly/fcc-cats" alt="Five cats looking around a field.">
          <figcaption>Cats <strong>hate</strong> other cats.</figcaption>  
        </figure>
      </section>
      <section>
        <h2>Cat Form</h2>
        <form action="https://freecatphotoapp.com/submit-cat-photo">
          --fcc-editable-region--
          <fieldset>
            <legend>Is your cat an indoor or outdoor cat?</legend>
            <label><input id="indoor" type="radio" name="indoor-outdoor" value="indoor"> Indoor</label>
            <label><input id="outdoor" type="radio" name="indoor-outdoor" value="outdoor"> Outdoor</label>
          </fieldset>
          <input type="text" name="catphotourl" placeholder="cat photo URL" required>
          <button type="submit">Submit</button>
          --fcc-editable-region--
        </form>
      </section>
    </main>
  </body>
</html>
```

</div>
</section>
