## Basic Example

```JavaScript
import { expect } from 'chai';
import nock from 'nock'
import request from 'request-promise';

describe('Basic Example', () => {
  const host = 'https://launchlibrary.net';
  const path = '/1.2/rocket/falcon';
  const expectedResponse = { rockets:[{ id:1, name:'Falcon 9 v1.1' }]};

  it('should reply with expected response', async () => {
    nock(host).get(path).reply(200, expectedResponse);
    const actual = await request.get(`${host}${path}`);
    expect(actual).to.equal(expectedResponse); // passes
  });
});
```
