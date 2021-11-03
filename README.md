# template-osbooks

Use this repository template to create an "osbooks" repository for migration of content from CNX Archive to Github.

**NOTE:** If you want to create an entirely new book (not move one from legacy) use the [/template-osbooks-new](https://github.com/openstax/template-osbooks-new/) repo

[Full list of **osbooks repositories**](https://github.com/openstax?q=osbooks) via Github Search.

Note: "osbook(s)" repository" and "content repository" can be used interchangably

### Overview of Steps

1. **Create osbook repository** - by using this template repository.
2. **Seed osbook repository** - by updating files the _content synchronization pipeline_ looks for to sync content from archive to github.
3. **Finalize osbook repository** - by creating a github issue to enable syncing of content from archive to github, one osbook per github issue.

---

## Create osbook repository

1. On GitHub, navigate to the main page of this repository.
2. Above the file list, click **Use this template**.
3. In the _Owner_ drop-down menu, select **openstax**.
4. Name the Repository:

   - _osbooks-**book-name**_, if repo contains only one collection, or
   - _osbooks-**book-name**-bundle_, if repo contains more than one collection

   Note: Repository names can be changed at a later time. _Description_ can be left blank.

5. Set repository visibility to **Private**.

6. Leave **Include all branches** unchecked, this template repository only has one branch.

7. Click **Create repository from template**.

## Seed osbook repository

Once the content repo is created:

1. Fill out the `META-INF/books.xml`:

   - Should contain atleast one `<book />` tag
   - Where `<book />` contains:
     - _slug_: determined by CM
     - _collection-id_: `col#####`
     - _href_: `"../collections/<slug>.collection.xml"`

   `books.xml` example

   ```
   <container xmlns="https://openstax.org/namespaces/book-container" version="1">
       <book slug="college-algebra" collection-id="col11759" href="../collections/college-algebra.collection.xml" />
       <book slug="precalculus" collection-id="col11667" href="../collections/precalculus.collection.xml" />
       <book slug="precalculus-coreq" collection-id="col32026" href="../collections/precalculus-coreq.collection.xml" />
   </container>
   ```

2. Copy/Paste one of the following into `LICENSE` file:

   - [CC-BY 4.0](https://github.com/openstax/content-synchronizer/blob/main/licenses/by-4.0)
   - [CC-BY-NC-SA 4.0](https://github.com/openstax/content-synchronizer/blob/main/licenses/by-nc-sa-4.0)
   - [CC-SA 4.0](https://github.com/openstax/content-synchronizer/blob/main/licenses/by-sa-4.0)

3. Change permissions with manage permissions
   1. On GitHub, navigate to the main page of this repository.
   2. On top navigation tabs, click **Settings**.
   3. On left navigation, click **Manage access**.
   4. Using the Manage Acccess panel, to add:
      - openstax/ce-all, Role: Write
      - openstax/content-managers, Role: Admin
      - openstax/ce-admins, Role: Admin
      - {vendor account}, Role: Write (Note: find the book's vendor under column C [here](https://docs.google.com/spreadsheets/d/1dVpPsE2wTIZyoC4n8GnooqpntC2IZDTjcSdNMPycfB0/edit#gid=254689054)).
         - Wisewire: `ww-openstax`
         - MPS: `mps-openstax`
         - Six Red Marbles (SRM): `srm-openstax`

## Finalize osbook repository

1. Navigate to [Create Issue for Repo Sync](https://github.com/openstax/cnx/issues/new?assignees=&labels=&template=task.md)
2. Title issue "Sync Content Repo `<osbook-repo-name>`"
3. Copy and Paste task.md into the body of issue:
   `task.md`

   ```
   ## Description

   ### Set up for Syncing for following Content Repo:
   Name of Content Repo: <!-- Name of Content Repo -->
   Link of Content Repo: <!-- Link to Content Repo -->

   ## Acceptance Criteria

   - [ ] [Sync pipeline set up](https://github.com/openstax/content-synchronizer#quick-start)
   - [ ]  Initial content sync is successful
   - [ ] "CE: Github Repo Stable Sync" column on [Github/POET transition plan spreadsheet](https://docs.google.com/spreadsheets/d/1qbkcpdpION-uN8GWW3zpanpunq4pjwqmVDGPOBhNW-8/edit#gid=0) is updated with hyperlink:
   - _text_: Date of first successful pipeline job
   - _link_: Link to pipeline

   ```

4. Update the following, in the issue body:

   - `<!-- Name of Content Repo -->`
   - `<!-- Link to Content Repo -->`

5. Click, **Submit New Issue**

### Once a new issue is submitted this kicks off the workflow to sync the content and eventually get it ready for [POET](https://poet.openstax.org/).

---

## Resources

- [Github/ POET Transition Plan](https://docs.google.com/spreadsheets/d/1qbkcpdpION-uN8GWW3zpanpunq4pjwqmVDGPOBhNW-8/edit#gid=0) (google spreadsheet)
- [Content Synchronizer](https://github.com/openstax/content-synchronizer) (github repo)
- [Content Repo Migration/ Creation Process](https://openstax.atlassian.net/wiki/spaces/CE/pages/1655209985/Migrate+Seed+Books+with+Github+for+POET) (confluence documentation)
- [Full List of Osbooks Repos](https://github.com/openstax?q=osbooks) (github search)
- [Template Repo for New Book](https://github.com/openstax/template-osbooks) (this github repo)
- [Creating a Repository from Template](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template) (github documentation)
