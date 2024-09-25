# Check that the commit title does not exceed 50 characters
git.commits.each do |commit|
  title = commit.message.split("\n").first
  if title.length > 50
    fail("Commit title exceeds 50 characters: '#{title}'")
  end

  # Check that there is a blank line between the title and the description
  if commit.message.split("\n").length > 1
    unless commit.message.split("\n")[1].strip.empty?
      fail("There must be a blank line between the commit title and description.")
    end
  end

  # Check that the description is at least 5 characters long
  description = commit.message.split("\n")[2..-1].join("\n").strip
  if description.length < 5
    fail("The commit description must be at least 5 characters long.")
  end

  # Check that no line in the description exceeds 72 characters
  description.each_line do |line|
    if line.length > 72
      warn("A line in the description exceeds 72 characters: '#{line.strip}'")
    end
  end
end
