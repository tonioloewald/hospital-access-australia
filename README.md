# Hospital Access Australia

The goal of this project is to graphically display the distribution of intensive care services in Australia.

As of now, the map displays the position of hospitals as red circles, and ICU availability as a heatmap.

Data used was obtained via:

### [List of Hospitals in Australia](https://en.wikipedia.org/wiki/List_of_hospitals_in_Australia)

- Captured text from page and converted it to JSON using grep.
- Added Google Places Data

### [College of Intensive Care Medicine of Australia and New Zealand](https://www.cicm.org.au/Hospitals/Accredited-Sites-Accordion/Accredited-Units#Classifications)

<td style="width:357px;"><strong>North District Hospital</strong><br />
      9 Po Kin Road<br />
      Sheung Shui NEW TERRITORIES<br />
      HONG KONG</td>
      <td style="width:94px;">Dr Koon Lam</td>
      <td style="width:113px;">Koon Lam</td>
      <td style="width:85px;">BASIC</td>
      <td style="width:95px;">Foundation</td>


- Ran the following scriptlet in the page:

var icus = [];
document.querySelectorAll('td[style*="357px"]').forEach(td => {
  icus.push({institution: td.querySelector('strong').textContent, location: td.textContent})
});
window.document.body.innerHTML = `<pre>${JSON.stringify(icus, false, 2)}</pre>`;
